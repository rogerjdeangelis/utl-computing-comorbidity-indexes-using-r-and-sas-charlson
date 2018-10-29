# utl-computing-comorbidity-indexes-using-r-and-sas-charlson
Computing multiple comorbidity indexes using R and SAS.

    Computing multiple comorbidity indexes using R and SAS                                                                        
                                                                                                                                  
    SAS differs from the two R packages(which agree?).                                                                            
                                                                                                                                  
    It looks like SAS may be doing some double counting.                                                                          
    If you have diabetes with complications then perhaps                                                                          
    diabetes should not also be selected?                                                                                         
    This is why you need both programmers and clinicians.                                                                         
    Both R pckages do not count both.                                                                                             
                                                                                                                                  
    R has three packages to compute Charlson and Elixhauser indexes.                                                              
    They do both ICD9 and ICD10.                                                                                                  
                                                                                                                                  
    CHARLSON INDEX  (see below for documentation)                                                                                 
    --------------                                                                                                                
                                                                                                                                  
    Patient 2 comparison (ICD10)                                                                                                  
                                                                                                                                  
                        R Packages                                                                                                
                       ================                                                                                           
    CONDITION     SAS  CORMORBIDITY ICD                                                                                           
                                                                                                                                  
      AMI          1        1        1   Myocardial infarction                                                                    
      CHF          1        1        1   Congestive heart failure                                                                 
      PVD          1        1        1   Peripheral vascular disease                                                              
      CEVD         0        0        0   Cerebrovascular disease                                                                  
      DEMENTIA     0        0        0   Dementia                                                                                 
      COPD         0        0        0   Chronic pulmonary disease                                                                
      RHEUMD       0        0        0   Rheumatic disease                                                                        
      PUD          0        0        0   Pepticulcer disease                                                                      
      MLD          0        0        0   Mild liver disease                                                                       
      DIAB         1        1        0   Diabetes without complication                                                            
      DIABWC       1        1        1   Diabetes with chronic complication                                                       
      HP           0        0        0   Hemiplegia or paraplegia                                                                 
      REND         1        1        1   Renal disease                                                                            
      CANC         0        0        0   Any malignancy                                                                           
      MSLD         0        0        0   Moderate or severe liver disease                                                         
      METACANC     0        0        0   Metastatic solid tumour                                                                  
      AIDS         0        0        0   AIDS/HIV                                                                                 
                                                                                                                                  
      SCORE        6**      5        5   NUMBER OF CONDITIONS                                                                     
                                                                                                                                  
      INDEX                 4            INDEX                                                                                    
      WSCORE                7            WEIGHTED SCORE                                                                           
      WINDEX                4            WEIGHTED INDEX                                                                           
                                                                                                                                  
    ** should be 5                                                                                                                
                                                                                                                                  
                                                                                                                                  
    CHARLSON INDEX                                                                                                                
    --------------                                                                                                                
                                                                                                                                  
    Many variations of the Charlson comorbidity index have been presented,                                                        
    as outlined by Sharabiani et al. in their systematic review. comorbidity                                                      
    computes the Quan et al. version of the Charlson score for both ICD-9-CM                                                      
    and ICD-10 coding systems, as outlined in their paper from 2005; in the next                                                  
    subsections, we present the different ICD codes utilised by comorbidity. Categorisation of                                    
    scores and weighted scores is based on work by Menendez et al.                                                                
                                                                                                                                  
                                                                                                                                  
    ELIXHAUSER INDEX                                                                                                              
    ================                                                                                                              
                                                                                                                                  
    The Elixhauser comorbidity index, analogously as the Charlson comorbidity                                                     
    index, is a method for measuring patient comorbidity based on ICD-9-CM                                                        
    and ICD-10 diagnosis codes found in administrative data developed by                                                          
    Elixhauser et al. in 1998. Over time, there have been changes to the                                                          
    Index based on different research. For instance:                                                                              
                                                                                                                                  
    the original index was developed with 30 categories. Now there are                                                            
    variants with 31 categories (Garland et al., 2012);                                                                           
    the list of specific ICD diagnosis codes that are used to identify                                                            
    different categories of comorbidity have been modified and updated                                                            
    from ICD-9-CM to work with ICD-10 coding (Quan et al., 2005);                                                                 
    weighting algorithms were developed, based on the association between                                                         
    comorbidity and death, in order to produce an overall score for the                                                           
    Elixhauser index (van Walraven et al., 2009; Moore et al., 2016).                                                             
    comorbidity is using the coding definition of Quan et al. (2005) for                                                          
    both ICD-9-CM and ICD-10 coding systems. The weighting is based on work by                                                    
    Moore et al. (2016); however, as the AHRQ Elixhauser comorbidity score                                                        
    only includes 29 comorbidites and not 31 (as in the Quan et al. version),                                                     
    we included weights from van Walraven et al. for the missing comorbidities.                                                   
    The actual codes and weights utilised by comorbidity are introduced                                                           
    in the next subsections.                                                                                                      
    Finally, the categorisation of scores and                                                                                     
    weighted scores is based on work by Menendez et al.                                                                           
                                                                                                                                  
    *_           _                                                                                                                
    (_)_ __   __| | _____  _____  ___                                                                                             
    | | '_ \ / _` |/ _ \ \/ / _ \/ __|                                                                                            
    | | | | | (_| |  __/>  <  __/\__ \                                                                                            
    |_|_| |_|\__,_|\___/_/\_\___||___/                                                                                            
      ____ _                _                   _         _ _  ___                                                                
     / ___| |__   __ _ _ __| |___  ___  _ __   (_) ___ __| / |/ _ \                                                               
    | |   | '_ \ / _` | '__| / __|/ _ \| '_ \  | |/ __/ _` | | | | |                                                              
    | |___| | | | (_| | |  | \__ \ (_) | | | | | | (_| (_| | | |_| |                                                              
     \____|_| |_|\__,_|_|  |_|___/\___/|_| |_| |_|\___\__,_|_|\___/                                                               
                                                                                                                                  
    ;                                                                                                                             
                                                                                                                                  
    The ICD-10 codes used by comorbidity to compute the Charlson comorbidity index are:                                           
                                                                                                                                  
    Myocardial infarction: I21.x, I22.x, I25.2                                                                                    
                                                                                                                                  
    Congestive heart failure: I09.9, I11.0, I13.0, I13.2, I25.5,                                                                  
    I42.0, I42.5 - I42.9, I43.x, I50.x, P29.0                                                                                     
                                                                                                                                  
    Peripheral vascular disease: I70.x, I71.x, I73.1, I73.8, I73.9,                                                               
    I77.1, I79.0, I79.2, K55.1, K55.8, K55.9, Z95.8, Z95.9                                                                        
                                                                                                                                  
    Cerebrovascular disease: G45.x, G46.x, H34.0, I60.x - I69.x                                                                   
                                                                                                                                  
    Dementia: F00.x - F03.x, F05.1, G30.x, G31.1                                                                                  
                                                                                                                                  
    Chronic pulmonary disease: I27.8, I27.9, J40.x - J47.x, J60.x - J67.x, J68.4, J70.1, J70.3                                    
                                                                                                                                  
    Rheumatic disease: M05.x, M06.x, M31.5, M32.x - M34.x, M35.1, M35.3, M36.0                                                    
                                                                                                                                  
    Pepticulcer disease: K25.x - K28.x                                                                                            
                                                                                                                                  
    Mild liver disease: B18.x, K70.0 - K70.3, K70.9, K71.3 - K71.5,                                                               
    K71.7, K73.x, K74.x, K76.0, K76.2 - K76.4, K76.8, K76.9, Z94.4                                                                
                                                                                                                                  
    Diabetes without chronic complication: E10.0, E10.1, E10.6, E10.8,                                                            
    E10.9, E11.0, E11.1, E11.6, E11.8, E11.9, E12.0, E12.1, E12.6, E12.8,                                                         
    E12.9, E13.0, E13.1, E13.6, E13.8, E13.9, E14.0, E14.1, E14.6, E14.8, E14.9                                                   
                                                                                                                                  
    Diabetes with chronic complication: E10.2 - E10.5, E10.7, E11.2 - E11.5,                                                      
    E11.7, E12.2 - E12.5, E12.7, E13.2 - E13.5, E13.7, E14.2 - E14.5, E14.7                                                       
                                                                                                                                  
    Hemiplegia or paraplegia: G04.1, G11.4, G80.1, G80.2, G81.x, G82.x, G83.0 - G83.4, G83.9                                      
                                                                                                                                  
    Renal disease: I12.0, I13.1, N03.2 - N03.7, N05.2 - N05.7, N18.x, N19.x,                                                      
    N25.0, Z49.0 - Z49.2, Z94.0, Z99.2                                                                                            
                                                                                                                                  
    Any malignancy, including lymphoma and leukemia, except malignant neoplasm of skin:                                           
    C00.x - C26.x, C30.x - C34.x, C37.x - C41.x, C43.x, C45.x - C58.x,                                                            
    C60.x - C76.x, C81.x - C85.x, C88.x, C90.x - C97.x                                                                            
                                                                                                                                  
    Moderate or severe liver disease: I85.0, I85.9, I86.4, I98.2,                                                                 
    K70.4, K71.1, K72.1, K72.9, K76.5, K76.6, K76.7                                                                               
                                                                                                                                  
    Metastatic solid tumour: C77.x - C80.x                                                                                        
                                                                                                                                  
    AIDS/HIV: B20.x - B22.x, B24.x                                                                                                
                                                                                                                                  
                                                                                                                                  
    *_____ _ _      _                                 _         _ _  ___                                                          
    | ____| (_)_  _| |__   __ _ _   _ ___  ___ _ __  (_) ___ __| / |/ _ \                                                         
    |  _| | | \ \/ / '_ \ / _` | | | / __|/ _ \ '__| | |/ __/ _` | | | | |                                                        
    | |___| | |>  <| | | | (_| | |_| \__ \  __/ |    | | (_| (_| | | |_| |                                                        
    |_____|_|_/_/\_\_| |_|\__,_|\__,_|___/\___|_|    |_|\___\__,_|_|\___/                                                         
                                                                                                                                  
    ;                                                                                                                             
                                                                                                                                  
    ICD-10 codes                                                                                                                  
    The ICD-10 codes used by comorbidity to compute the Elixhauser comorbidity index are:                                         
                                                                                                                                  
    Congestive heart failure: I09.9, I11.0, I13.0, I13.2, I25.5, I42.0,                                                           
    I42.5 - I42.9, I43.x, I50.x, P29.0                                                                                            
                                                                                                                                  
    Cardiac arrhythmias: I44.1 - I44.3, I45.6, I45.9, I47.x - I49.x,                                                              
    R00.0, R00.1, R00.8, T82.1, Z45.0, Z95.0                                                                                      
                                                                                                                                  
    Valvular disease: A52.0, I05.x - I08.x, I09.1, I09.8, I34.x - I39.x,                                                          
    Q23.0 - Q23.3, Z95.2 - Z95.4                                                                                                  
                                                                                                                                  
    Pulmonary circulation disorders: I26.x, I27.x, I28.0, I28.8, I28.9                                                            
                                                                                                                                  
    Peripheral vascular disorders: I70.x, I71.x, I73.1, I73.8, I73.9, I77.1,                                                      
    I79.0, I79.2, K55.1, K55.8, K55.9, Z95.8, Z95.9                                                                               
                                                                                                                                  
    Hypertension, uncomplicated: I10.x                                                                                            
                                                                                                                                  
    Hypertension, complicated: I11.x - I13.x, I15.x                                                                               
                                                                                                                                  
    Paralysis: G04.1, G11.4, G80.1, G80.2, G81.x, G82.x, G83.0 - G83.4, G83.9                                                     
                                                                                                                                  
    Other neurological disorders: G10.x - G13.x, G20.x - G22.x, G25.4, G25.5,                                                     
    G31.2, G31.8, G31.9, G32.x, G35.x - G37.x, G40.x, G41.x, G93.1, G93.4, R47.0, R56.x                                           
                                                                                                                                  
    Chronic pulmonary disease: I27.8, I27.9, J40.x - J47.x, J60.x - J67.x, J68.4, J70.1, J70.3                                    
                                                                                                                                  
    Diabetes, uncomplicated: E10.0, E10.1, E10.9, E11.0, E11.1, E11.9, E12.0,                                                     
    E12.1, E12.9, E13.0, E13.1, E13.9, E14.0, E14.1, E14.9                                                                        
                                                                                                                                  
    Diabetes, complicated: E10.2 - E10.8, E11.2 - E11.8, E12.2 - E12.8, E13.2 - E13.8, E14.2 - E14.8                              
                                                                                                                                  
    Hypothyroidism: E00.x - E03.x, E89.0                                                                                          
                                                                                                                                  
    Renal failure: I12.0, I13.1, N18.x, N19.x, N25.0, Z49.0 - Z49.2, Z94.0, Z99.2                                                 
                                                                                                                                  
    Liver disease: B18.x, I85.x, I86.4, I98.2, K70.x, K71.1, K71.3 - K71.5,                                                       
    K71.7, K72.x - K74.x, K76.0, K76.2 - K76.9, Z94.4                                                                             
                                                                                                                                  
    Peptic ulcer disease, excluding bleeding: K25.7, K25.9, K26.7, K26.9, K27.7, K27.9, K28.7, K28.9                              
                                                                                                                                  
    AIDS/HIV: B20.x - B22.x, B24.x                                                                                                
                                                                                                                                  
    Lymphoma: C81.x - C85.x, C88.x, C96.x, C90.0, C90.2                                                                           
                                                                                                                                  
    Metastatic cancer: C77.x - C80.x                                                                                              
                                                                                                                                  
    Solid tumor without metastasis: C00.x - C26.x, C30.x - C34.x, C37.x - C41.x,                                                  
    C43.x, C45.x - C58.x, C60.x - C76.x, C97.x                                                                                    
                                                                                                                                  
    Rheumatoid arthritis/collagen vascular diseases: L94.0, L94.1, L94.3, M05.x,                                                  
    M06.x, M08.x, M12.0, M12.3, M30.x, M31.0 - M31.3, M32.x - M35.x, M45.x, M46.1, M46.8, M46.9                                   
                                                                                                                                  
    Coagulopathy: D65 - D68.x, D69.1, D69.3 - D69.6                                                                               
                                                                                                                                  
    Obesity: E66.x                                                                                                                
                                                                                                                                  
    Weight loss: E40.x - E46.x, R63.4, R64                                                                                        
                                                                                                                                  
    Fluid and electrolyte disorders: E22.2, E86.x, E87.x                                                                          
                                                                                                                                  
    Blood loss anemia: D50.0                                                                                                      
                                                                                                                                  
    Deficiency anemia: D50.8, D50.9, D51.x - D53.x                                                                                
                                                                                                                                  
    Alcohol abuse: F10, E52, G62.1, I42.6, K29.2, K70.0, K70.3, K70.9, T51.x, Z50.2, Z71.4, Z72.1                                 
                                                                                                                                  
    Drug abuse: F11.x - F16.x, F18.x, F19.x, Z71.5, Z72.2                                                                         
                                                                                                                                  
    Psychoses: F20.x, F22.x - F25.x, F28.x, F29.x, F30.2, F31.2, F31.5                                                            
                                                                                                                                  
    Depression: F20.4, F31.3 - F31.5, F32.x, F33.x, F34.1, F41.2, F43.2                                                           
                                                                                                                                  
    I will look into the SAS Macro. These packages seem to have goo support.                                                      
                                                                                                                                  
    *                 ___     ____                                                                                                
     ___  __ _ ___   ( _ )   |  _ \                                                                                               
    / __|/ _` / __|  / _ \/\ | |_) |                                                                                              
    \__ \ (_| \__ \ | (_>  < |  _ <                                                                                               
    |___/\__,_|___/  \___/\/ |_| \_\                                                                                              
                                                                                                                                  
    ;                                                                                                                             
                                                                                                                                  
      1. SAS macro _charlsonicd10 (does not agree with mutiple R pacakes)                                                         
         Does not due weighting. May be more roll your oun macros? Macro on end                                                   
                                                                                                                                  
      2. cormorbidity (flexible does scoring and weights)                                                                         
         https://cran.r-project.org/web/packages/comorbidity/comorbidity.pdf                                                      
                                                                                                                                  
      3. icd  (many options with several indexes - can do scoring)                                                                
         https://cran.r-project.org/web/packages/icd/index.html                                                                   
                                                                                                                                  
         Options for icd package                                                                                                  
                                                                                                                                  
         icd10_comorbid            : ICD-10 comorbidities                                                                         
         icd9_comorbid             : Get comorbidities from data.frame of ICD-9 codes                                             
         icd9_comorbid_ahrq        : AHRQ comorbidities for ICD-9 codes                                                           
         icd10_comorbid_ahrq       : AHRQ comorbidities for ICD-10 codes                                                          
         icd9_comorbid_elix        : Elixhauser comorbidities for ICD-9 codes                                                     
         icd10_comorbid_elix       : Elixhauser comorbidities for ICD-10 codes                                                    
         icd9_comorbid_quan_elix   : Quan's Elixhauser comorbidities for ICD-9 codes                                              
         icd10_comorbid_quan_elix  : Quan's Elixhauser comorbidities for ICD-10 codes                                             
         icd9_comorbid_quan_deyo   : Quan's Deyo (Charlson) comorbidities for ICD-9 codes                                         
         icd10_comorbid_quan_deyo  : Quan's Deyo (Charlson) comorbidities for ICD-10 codes                                        
         icd9_comorbid_charlson    : Currently synonym for icd9_comorbid_quan_deyo                                                
         icd10_comorbid_charlson   : Currently synonym for icd10_comorbid_quan_deyo                                               
         comorbid_ccs              : Use AHRQ CCS for comorbidity classification                                                  
         icd9_comorbid_ccs         : Compute AHRQ Clinical Classifications Software (CCS) scores from ICD-9 codes                 
         icd10_comorbid_ccs        : Compute AHRQ Clinical Classifications Software (CCS) scores from ICD-10 codes                
         comorbid_ahrq             : AHRQ comorbidities, infers whether to use ICD-9 or ICD-10 codes                              
         comorbid_elix             : Elixhauser comorbidities, infers whether to use ICD-9 or ICD-10 codes                        
         comorbid_quan_elix        : Quan's Elixhauser comorbidities, infers whether to use ICD-9 or ICD-10 codes                 
         comorbid_quan_deyo        : Quan's Deyo (Charlson) comorbidities, infers whether to use ICD-9 or ICD-10 codes            
         comorbid_charlson         : Calculate comorbidities using Charlson categories according to Quan/Deyo ICD categories.     
                                                                                                                                  
     Other R Comorbidity Packages                                                                                                 
                                                                                                                                  
      3. medicalrisk (only icd9)                                                                                                  
         https://cran.r-project.org/web/packages/medicalrisk/medicalrisk.pdf                                                      
                                                                                                                                  
      4. cormoRbity (more for built in  analysis functions - plots, heatmaps and stats?)                                          
         https://academic.oup.com/bioinformatics/article/34/18/3228/4979545                                                       
         library(devtools)                                                                                                        
         install_github("aGutierrezSacristan/comoRbidity")                                                                        
                                                                                                                                  
    *_                   _                                                                                                        
    (_)_ __  _ __  _   _| |_                                                                                                      
    | | '_ \| '_ \| | | | __|                                                                                                     
    | | | | | |_) | |_| | |_                                                                                                      
    |_|_| |_| .__/ \__,_|\__|                                                                                                     
            |_|                                                                                                                   
    ;                                                                                                                             
    INPUT  (ICD10 Codes)                                                                                                          
    =====================                                                                                                         
                                                                                                                                  
    data sd1.have;                                                                                                                
     input pat icd10$;                                                                                                            
    cards4;                                                                                                                       
    1 I0981                                                                                                                       
    1 I509                                                                                                                        
    1 R000                                                                                                                        
    1 Z741                                                                                                                        
    1 Z66                                                                                                                         
    1 I071                                                                                                                        
    1 I4891                                                                                                                       
    1 I272                                                                                                                        
    1 I313                                                                                                                        
    1 I120                                                                                                                        
    1 N185                                                                                                                        
    1 D649                                                                                                                        
    1 M6281                                                                                                                       
    1 Z9181                                                                                                                       
    1 I742                                                                                                                        
    1 Z7901                                                                                                                       
    1 I739                                                                                                                        
    1 M150                                                                                                                        
    1 G5600                                                                                                                       
    1 F419                                                                                                                        
    1 M4806                                                                                                                       
    1 Z85038                                                                                                                      
    1 Z9049                                                                                                                       
    1 C3490                                                                                                                       
    1 Z923                                                                                                                        
    2 J690                                                                                                                        
    2 J9601                                                                                                                       
    2 I214                                                                                                                        
    2 N179                                                                                                                        
    2 L97429                                                                                                                      
    2 M86672                                                                                                                      
    2 J1289                                                                                                                       
    2 E875                                                                                                                        
    2 B9729                                                                                                                       
    2 I4510                                                                                                                       
    2 I255                                                                                                                        
    2 E8770                                                                                                                       
    2 I129                                                                                                                        
    2 E1122                                                                                                                       
    2 N183                                                                                                                        
    2 E1140                                                                                                                       
    2 E11621                                                                                                                      
    2 I2510                                                                                                                       
    2 I739                                                                                                                        
    2 E785                                                                                                                        
    2 F70                                                                                                                         
    2 G4733                                                                                                                       
    2 E039                                                                                                                        
    2 K219                                                                                                                        
    2 R6250                                                                                                                       
    3 I5023                                                                                                                       
    3 I110                                                                                                                        
    3 I350                                                                                                                        
    3 I480                                                                                                                        
    3 Z7982                                                                                                                       
    3 E119                                                                                                                        
    3 F0390                                                                                                                       
    3 K4091                                                                                                                       
    3 J449                                                                                                                        
    3 M069                                                                                                                        
    3 M1990                                                                                                                       
    3 H3530                                                                                                                       
    3 Z7984                                                                                                                       
    3 Z7952                                                                                                                       
    ;;;;                                                                                                                          
    run;quit;                                                                                                                     
                                                                                                                                  
    *_                                                                                                                            
    / |     ___  __ _ ___                                                                                                         
    | |    / __|/ _` / __|                                                                                                        
    | |_   \__ \ (_| \__ \                                                                                                        
    |_(_)  |___/\__,_|___/                                                                                                        
                                                                                                                                  
    ;                                                                                                                             
                                                                                                                                  
    libname sd1 "d:/sd1";                                                                                                         
                                                                                                                                  
    proc transpose data=sd1.have out=havXpo(drop=_name_);                                                                         
      by pat;                                                                                                                     
      var icd10;                                                                                                                  
    run;quit;                                                                                                                     
                                                                                                                                  
    to 40 obs WORK.HAVXPO total obs=3                                                                                             
                                                                                                                                  
     PAT COL1  COL2  COL3 COL4 COL5        COL25                                                                                  
                                                                                                                                  
      1  I0981 I509  R000 Z741 Z66    ...  Z923                                                                                   
      2  J690  J9601 I214 N179 L97429 ...  R6250                                                                                  
      3  I5023 I110  I350 I480 Z7982  ...                                                                                         
                                                                                                                                  
                                                                                                                                  
    * WILL APPEND TO &pgm.apn;                                                                                                    
    proc datasets lib=sd1;                                                                                                        
    delete &pgm.apn;                                                                                                              
    run;quit;                                                                                                                     
                                                                                                                                  
    data log;                                                                                                                     
                                                                                                                                  
      do patient=1 to 3;                                                                                                          
                                                                                                                                  
          call symputx('patient',patient);                                                                                        
                                                                                                                                  
          rc=dosubl('                                                                                                             
             data subset;                                                                                                         
                 set havXpo(firstobs=&patient obs=&patient);                                                                      
             run;quit;                                                                                                            
                                                                                                                                  
             %_CharlsonICD10 (                                                                                                    
               DATA      =subset,                                                                                                 
               out       =&pgm.patient,                                                                                           
               dx        =col1-col25,                                                                                             
               type      =off,                                                                                                    
               debug     =off);                                                                                                   
                                                                                                                                  
             data cutCde(rename=tot_grp=numConditions);                                                                           
                set &pgm.patient;                                                                                                 
                drop col: I;                                                                                                      
             run;quit;                                                                                                            
                                                                                                                                  
             proc append data=cutCde base=sd1.&pgm.apn;                                                                           
             run;quit;                                                                                                            
                                                                                                                                  
             %let cc=&syserr;                                                                                                     
          ');                                                                                                                     
                                                                                                                                  
         if symgetn("cc") =0 then status="Charlson created  ";                                                                    
          else status="Charlson failed  ";                                                                                        
          output;                                                                                                                 
                                                                                                                                  
                                                                                                                                  
      end;                                                                                                                        
                                                                                                                                  
    run;quit;                                                                                                                     
                                                                                                                                  
    /*                                                                                                                            
     WORK.log total obs=3                                                                                                         
                                                                                                                                  
     PATIENT    RC         STATUS                                                                                                 
                                                                                                                                  
        1        0    Charlson created                                                                                            
        2        0    Charlson created                                                                                            
        3        0    Charlson created                                                                                            
                                                                                                                                  
                                                                                                                                  
     SD1.CCI_MORBID2APN total obs=3                                                                                               
                                                                                                                                  
                                                                                                                                  
     PAT CC_GRP_1 CC_GRP_2 CC_GRP_3 ... CC_GRP_25   NUMCONDITIONS                                                                 
                                                                                                                                  
      1      0        1        1    ...     0             4                                                                       
      2      1        1        1    ...     0             6  ** Problem?                                                          
      3      0        1        0    ...     1             5                                                                       
                                                                                                                                  
    */                                                                                                                            
                                                                                                                                  
    proc transpose data=sd1.&pgm.apn                                                                                              
      out=cci.&pgm.apnxpo;                                                                                                        
    id pat;                                                                                                                       
    var CC_G: num:;                                                                                                               
    run;quit;                                                                                                                     
                                                                                                                                  
    /*                                                                                                                            
    SD1.CCI_MORBID2APNXPO total obs=18                    Patients                                                                
                                                                                                                                  
       _LABEL_                                        _1    _2    _3                                                              
                                                                                                                                  
       Myocardial Infarction                           0     1     0                                                              
       Congestive Heart Failure                        1     1     1                                                              
       Periphral Vascular Disease                      1     1     0                                                              
       Cerebrovascular Disease                         0     0     0                                                              
       Dementia                                        0     0     1                                                              
       Chronic Pulmonary Disease                       0     0     1                                                              
       Connective Tissue Disease-Rheumatic Disease     0     0     1                                                              
       Peptic Ulcer Disease                            0     0     0                                                              
       Mild Liver Disease                              0     0     0                                                              
       Diabetes without complications                  0     1     1                                                              
       Diabetes with complications                     0     1     0                                                              
       Paraplegia and Hemiplegia                       0     0     0                                                              
       Renal Disease                                   1     1     0                                                              
       Cancer                                          1     0     0                                                              
       Moderate or Severe Liver Disease                0     0     0                                                              
       Metastatic Carcinoma                            0     0     0                                                              
       AIDS/HIV                                        0     0     0                                                              
                                                      ==    ==    ==                                                              
       Total CCI Groups per record                     4     6**   5                                                              
                                                                                                                                  
      ** Problem                                                                                                                  
                                                                                                                                  
    */                                                                                                                            
                                                                                                                                  
    *____                                     _     _     _ _ _                                                                   
    |___ \      ___ ___  _ __ ___   ___  _ __| |__ (_) __| (_) |_ _   _                                                           
      __) |    / __/ _ \| '_ ` _ \ / _ \| '__| '_ \| |/ _` | | __| | | |                                                          
     / __/ _  | (_| (_) | | | | | | (_) | |  | |_) | | (_| | | |_| |_| |                                                          
    |_____(_)  \___\___/|_| |_| |_|\___/|_|  |_.__/|_|\__,_|_|\__|\__, |                                                          
                                                                  |___/                                                           
    ;                                                                                                                             
                                                                                                                                  
    * Does both Charlson and Elixhauser indices;                                                                                  
                                                                                                                                  
    %utl_submit_r64('                                                                                                             
    library(comorbidity);                                                                                                         
    library(haven);                                                                                                               
    library(SASxport);                                                                                                            
    have<-read_sas("d:/sd1/have.sas7bdat");                                                                                       
    head(have);                                                                                                                   
    c10 <- comorbidity(x = have, id = "PAT", code = "ICD10", score = "charlson");                                                 
    c10;                                                                                                                          
    write.xport(c10,file="d:/xpt/cci_charlson10.xpt");                                                                            
    e10 <- comorbidity(x = have, id = "PAT", code = "ICD10", score = "elixhauser");                                               
    e10;                                                                                                                          
    write.xport(e10,file="d:/xpt/cci_elixhauser10.xpt");                                                                          
    ');                                                                                                                           
                                                                                                                                  
    /* in R                                                                                                                       
      PAT ami chf pvd cevd dementia copd rheumd pud mld diab diabwc hp rend canc                                                  
    1   1   0   1   1    0        0    0      0   0   0    0      0  0    1    1                                                  
    2   2   1   1   1    0        0    0      0   0   0    1      1  0    1    0                                                  
    3   3   0   1   0    0        1    1      1   0   0    1      0  0    0    0                                                  
      msld metacanc aids score index wscore windex                                                                                
    1    0        0    0     4   3-4      6    >=5                                                                                
    2    0        0    0     5   >=5      7    >=5                                                                                
    3    0        0    0     5   >=5      5    >=5                                                                                
    */                                                                                                                            
                                                                                                                                  
    libname c10 xport "d:/xpt/cci_charlson10.xpt";                                                                                
    libname e10 xport "d:/xpt/cci_elixhauser10.xpt";                                                                              
                                                                                                                                  
    data c10;                                                                                                                     
      set c10.c10;                                                                                                                
    run;quit;                                                                                                                     
                                                                                                                                  
    data e10;                                                                                                                     
      set e10.e10;                                                                                                                
    run;quit;                                                                                                                     
                                                                                                                                  
    proc transpose data=c10 out=c10xpo;                                                                                           
     id pat;                                                                                                                      
    run;quit;                                                                                                                     
                                                                                                                                  
    /*                                                                                                                            
     WORK.C10XPO total obs=21                                                                                                     
                                                                                                                                  
      _NAME_      _1    _2    _3                                                                                                  
                                                                                                                                  
      AMI          0     1     0                                                                                                  
      CHF          1     1     1                                                                                                  
      PVD          1     1     0                                                                                                  
      CEVD         0     0     0                                                                                                  
      DEMENTIA     0     0     1                                                                                                  
      COPD         0     0     1                                                                                                  
      RHEUMD       0     0     1                                                                                                  
      PUD          0     0     0                                                                                                  
      MLD          0     0     0                                                                                                  
      DIAB         0     1     1                                                                                                  
      DIABWC       0     1     0                                                                                                  
      HP           0     0     0                                                                                                  
      REND         1     1     0                                                                                                  
      CANC         1     0     0                                                                                                  
      MSLD         0     0     0                                                                                                  
      METACANC     0     0     0                                                                                                  
      AIDS         0     0     0                                                                                                  
      SCORE        4     5     5                                                                                                  
      INDEX        3     4     4                                                                                                  
      WSCORE       6     7     5                                                                                                  
      WINDEX       4     4     4                                                                                                  
    */                                                                                                                            
                                                                                                                                  
    proc transpose data=e10 out=e10xpo;                                                                                           
     id pat;                                                                                                                      
    run;quit;                                                                                                                     
                                                                                                                                  
    proc print data=c10xpo ;                                                                                                      
    run;quit;                                                                                                                     
                                                                                                                                  
    proc print data=e10xpo ;                                                                                                      
    run;quit;                                                                                                                     
                                                                                                                                  
                                                                                                                                  
                                                                                                                                  
    *_____    _         _ _  ___                                                                                                  
    |___ /   (_) ___ __| / |/ _ \                                                                                                 
      |_ \   | |/ __/ _` | | | | |                                                                                                
     ___) |  | | (_| (_| | | |_| |                                                                                                
    |____(_) |_|\___\__,_|_|\___/                                                                                                 
                                                                                                                                  
    ;                                                                                                                             
                                                                                                                                  
    %utl_submit_r64('                                                                                                             
    library(icd);                                                                                                                 
    library(haven);                                                                                                               
    library(SASxport);                                                                                                            
    have<-read_sas("d:/sd1/have.sas7bdat");                                                                                       
    library(sqldf);                                                                                                               
    pts10 <- icd_long_data(                                                                                                       
      visit_name = have$PAT,                                                                                                      
      icd_name =have$ICD10);                                                                                                      
    pts10;                                                                                                                        
    res<-1*as.data.frame(icd::icd10_comorbid_quan_deyo(pts10));                                                                   
    head(res);                                                                                                                    
    write.xport(res,file="d:/xpt/cci_charlsonicd.xpt");                                                                           
    ');                                                                                                                           
                                                                                                                                  
    /* in R                                                                                                                       
      MI CHF PVD Stroke Dementia Pulmonary Rheumatic PUD LiverMild DM DMcx                                                        
    1  0   1   1      0        0         0         0   0         0  0    0                                                        
    2  1   1   1      0        0         0         0   0         0  0    1                                                        
    3  0   1   0      0        1         1         1   0         0  1    0                                                        
      Paralysis Renal Cancer LiverSevere Mets HIV                                                                                 
    1         0     1      1           0    0   0                                                                                 
    2         0     1      0           0    0   0                                                                                 
    3         0     0      0           0    0   0                                                                                 
    */                                                                                                                            
                                                                                                                                  
    libname cda xport "d:/xpt/cci_charlsonicd.xpt";                                                                               
                                                                                                                                  
    data cda;                                                                                                                     
      set cda.res ;                                                                                                               
      array nums[*] _numeric_;                                                                                                    
      numconditions=sum(of nums[*]);                                                                                              
      pat=_n_;                                                                                                                    
    run;quit;                                                                                                                     
                                                                                                                                  
    proc transpose data=cda out=cdaxpo;                                                                                           
     id pat;                                                                                                                      
    run;quit;                                                                                                                     
                                                                                                                                  
    /*                                                                                                                            
     WORK.CDAXPO total obs=18                                                                                                     
                                                                                                                                  
      _NAME_           _1    _2    _3                                                                                             
                                                                                                                                  
      MI                0     1     0                                                                                             
      CHF               1     1     1                                                                                             
      PVD               1     1     0                                                                                             
      STROKE            0     0     0                                                                                             
      DEMENTIA          0     0     1                                                                                             
      PULMONAR          0     0     1                                                                                             
      RHEUMATI          0     0     1                                                                                             
      PUD               0     0     0                                                                                             
      LIVERMIL          0     0     0                                                                                             
      DM                0     0     1                                                                                             
      DMCX              0     1     0                                                                                             
      PARALYSI          0     0     0                                                                                             
      RENAL             1     1     0                                                                                             
      CANCER            1     0     0                                                                                             
      LIVERSEV          0     0     0                                                                                             
      METS              0     0     0                                                                                             
      HIV               0     0     0                                                                                             
                       ==    ==    ==                                                                                             
      NUMCONDITIONS     4     5     5                                                                                             
                                                                                                                                  
                                                                                                                                  
                                                                                                                                  
    *                                                                                                                             
     _ __ ___   __ _  ___ _ __ ___                                                                                                
    | '_ ` _ \ / _` |/ __| '__/ _ \                                                                                               
    | | | | | | (_| | (__| | | (_) |                                                                                              
    |_| |_| |_|\__,_|\___|_|  \___/                                                                                               
                                                                                                                                  
    ;                                                                                                                             
                                                                                                                                  
    %macro _CharlsonICD10 (DATA    =,     /* input data set */                                                                    
                           OUT     =,     /* output data set */                                                                   
                           dx      =diag01-diag25,     /* range of diagnosis variables (diag01-diag25) */                         
                           dxtype  =diagtype01-diagtype25,    /* range of diagnosis type variables                                
                                           (diagtype01-diagtype25) */                                                             
                           type    =off, /** on/off  turn on use of dxtype ***/                                                   
                           debug   =off ) ;                                                                                       
                                                                                                                                  
          %put Charlson Comorbidity Index Macro - ICD10 Codes ;                                                                   
          %put Manitoba Centre for Health Policy, Based on Code from Hude Quan University of Calgary ;                            
          %put Quan et al., Coding Algorithms for Defining Comorbidities ;                                                        
          %put     in ICD-9-CM and ICD-10 Administrative Data, Medical Care:43(11), Nov. 2005 p1130-1139 ;                        
          %put Version 1.0e February 23, 2007 ;                                                                                   
                                                                                                                                  
                                                                                                                                  
          %let debug = %lowcase(&debug) ;                                                                                         
          %let type = %lowcase(&type) ;                                                                                           
                                                                                                                                  
          %* put default options into &opts variable ;                                                                            
      %let opts=%sysfunc(getoption(mprint,keyword))                                                                               
            %sysfunc(getoption(notes,keyword)) ;                                                                                  
                                                                                                                                  
      %if &debug=1 | &debug=debug %then %do ;                                                                                     
                options mprint notes ;                                                                                            
                %end ;                                                                                                            
          %else %do ;                                                                                                             
                options nomprint nonotes ;                                                                                        
                %end ;                                                                                                            
                                                                                                                                  
          %* Check if previous data step, or procdure had an error and                                                            
           stop running the rates macro                                                                                           
          This assumes that the previous step is used in the macro.;                                                              
     %if %eval(&SYSERR>0) %then %goto out1 ;                                                                                      
                                                                                                                                  
      %* Check if input data exists ;                                                                                             
      %if &data= %str() %then %goto out2 ;                                                                                        
                                                                                                                                  
      %* if the output data set is not defined then define it as the input ;                                                      
      %if &out=  %then %let out=&data ;                                                                                           
                                                                                                                                  
      %if %index(&data,.) %then %do;                                                                                              
         %let libname=%scan(&data,1);                                                                                             
           %let data=%scan(&data,2);                                                                                              
           %end;                                                                                                                  
     %else %do ;                                                                                                                  
           %let libname=work ;                                                                                                    
           %let data=&data ;                                                                                                      
           %end ;                                                                                                                 
                                                                                                                                  
     %if %sysfunc(exist(&libname..&data)) ^= 1 %then %goto out3 ;                                                                 
                                                                                                                                  
          data &OUT;                                                                                                              
          set &DATA ;                                                                                                             
                                                                                                                                  
          /*  set up array for individual CCI group counters */                                                                   
          array CC_GRP (17) CC_GRP_1 - CC_GRP_17;                                                                                 
                                                                                                                                  
          /*  set up array for 25 diagnosis codes within a record  */                                                             
          array DX (*) &dx;                                                                                                       
                                                                                                                                  
          /*  set up array for 25 diagnosis type codes within a record */                                                         
            %if &type=on %then array DXTYPE (*) &dxtype; ;                                                                        
                                                                                                                                  
                                                                                                                                  
          /*  initialize all CCI group counters to zero */                                                                        
          do i = 1 to 17;                                                                                                         
             CC_GRP(i) = 0;                                                                                                       
          end;                                                                                                                    
                                                                                                                                  
          /*  check each patient record for the diagnosis codes in each CCI group */                                              
          do i = 1 to dim(dx) UNTIL (DX(i)=" ");     /* for each set of diagnoses codes */                                        
                                                                                                                                  
            /*  skip diagnosis if diagnosis type = "2" */                                                                         
                  %if &type=on %then if DXTYPE(i) ^="2" then DO; ;                                                                
                                                                                                                                  
                                                                                                                                  
               /* Myocardial Infarction */                                                                                        
               if DX(i) IN: ("I21", "I22","I252") then CC_GRP_1 = 1;                                                              
               LABEL CC_GRP_1 = "Myocardial Infarction";                                                                          
                                                                                                                                  
               /* Congestive Heart Failure */                                                                                     
               if DX(i) IN: ("I43","I50","I099","I110","I130","I132","I255","I420","I425","I426",                                 
                             "I427","I428","I429","P290") then CC_GRP_2 = 1;                                                      
               LABEL CC_GRP_2 = "Congestive Heart Failure";                                                                       
                                                                                                                                  
               /* Periphral Vascular Disease */                                                                                   
               if DX(i) IN: ("I70","I71","I731","I738","I739","I771","I790","I792","K551","K558",                                 
                             "K559","Z958","Z959") then CC_GRP_3 = 1;                                                             
               LABEL CC_GRP_3 = "Periphral Vascular Disease";                                                                     
                                                                                                                                  
               /* Cerebrovascular Disease */                                                                                      
               if DX(i) IN: ("G45","G46","I60","I61","I62","I63","I64","I65","I66","I67","I68",                                   
                             "I69","H340") then CC_GRP_4 = 1;                                                                     
               LABEL CC_GRP_4 = "Cerebrovascular Disease";                                                                        
                                                                                                                                  
               /* Dementia */                                                                                                     
               if DX(i) IN: ("F00","F01","F02","F03","G30","F051","G311")                                                         
                             then CC_GRP_5 = 1;                                                                                   
               LABEL CC_GRP_5 = "Dementia";                                                                                       
                                                                                                                                  
               /* Chronic Pulmonary Disease */                                                                                    
               if DX(i) IN: ("J40","J41","J42","J43","J44","J45","J46","J47","J60","J61","J62","J63",                             
                             "J64","J65","J66","J67""I278","I279","J684","J701","J703")                                           
                             then CC_GRP_6 = 1;                                                                                   
               LABEL CC_GRP_6 = "Chronic Pulmonary Disease";                                                                      
                                                                                                                                  
               /* Connective Tissue Disease-Rheumatic Disease */                                                                  
               if DX(i) IN: ("M05","M32","M33","M34","M06","M315","M351","M353","M360")                                           
                             then CC_GRP_7 = 1;                                                                                   
               LABEL CC_GRP_7 = "Connective Tissue Disease-Rheumatic Disease";                                                    
                                                                                                                                  
               /* Peptic Ulcer Disease */                                                                                         
               if DX(i) IN: ("K25","K26","K27","K28") then CC_GRP_8 = 1;                                                          
               LABEL CC_GRP_8 = "Peptic Ulcer Disease";                                                                           
                                                                                                                                  
               /* Mild Liver Disease */                                                                                           
               if DX(i) IN: ("B18","K73","K74","K700","K701","K702","K703","K709","K717","K713",                                  
                             "K714","K715","K760","K762","K763","K764","K768","K769","Z944")                                      
                             then CC_GRP_9 = 1;                                                                                   
               LABEL CC_GRP_9 = "Mild Liver Disease";                                                                             
                                                                                                                                  
               /* Diabetes without complications */                                                                               
               if DX(i) IN: ("E100","E101","E106","E108","E109","E110","E111","E116","E118","E119",                               
                             "E120","E121","E126","E128","E129","E130","E131","E136","E138","E139",                               
                             "E140","E141","E146","E148","E149") then CC_GRP_10 = 1;                                              
               LABEL CC_GRP_10 = "Diabetes without complications";                                                                
                                                                                                                                  
               /* Diabetes with complications */                                                                                  
               if DX(i) IN: ("E102","E103","E104","E105","E107","E112","E113","E114","E115","E117",                               
                             "E122","E123","E124","E125","E127","E132","E133","E134","E135","E137",                               
                             "E142","E143","E144","E145","E147") then CC_GRP_11 = 1;                                              
               LABEL CC_GRP_11 = "Diabetes with complications";                                                                   
                                                                                                                                  
               /* Paraplegia and Hemiplegia */                                                                                    
               if DX(i) IN: ("G81","G82","G041","G114","G801","G802","G830","G831","G832","G833",                                 
                             "G834","G839") then CC_GRP_12 = 1;                                                                   
               LABEL CC_GRP_12 = "Paraplegia and Hemiplegia";                                                                     
                                                                                                                                  
               /* Renal Disease */                                                                                                
               if DX(i) IN: ("N18","N19","N052","N053","N054","N055","N056","N057","N250","I120",                                 
                             "I131","N032","N033","N034","N035","N036","N037","Z490","Z491","Z492",                               
                             "Z940","Z992") then CC_GRP_13 = 1;                                                                   
               LABEL CC_GRP_13 = "Renal Disease";                                                                                 
                                                                                                                                  
               /* Cancer */                                                                                                       
               if DX(i) IN: ("C00","C01","C02","C03","C04","C05","C06","C07","C08","C09","C10","C11",                             
                             "C12","C13","C14","C15","C16","C17","C18","C19","C20","C21","C22","C23",                             
                             "C24","C25","C26","C30","C31","C32","C33","C34","C37","C38","C39","C40",                             
                             "C41","C43","C45","C46","C47","C48","C49","C50","C51","C52","C53","C54",                             
                             "C55","C56","C57","C58","C60","C61","C62","C63","C64","C65","C66","C67",                             
                             "C68","C69","C70","C71","C72","C73","C74","C75","C76","C81","C82","C83",                             
                             "C84","C85","C88","C90","C91","C92","C93","C94","C95","C96","C97")                                   
                             then CC_GRP_14 = 1;                                                                                  
               LABEL CC_GRP_14 = "Cancer";                                                                                        
                                                                                                                                  
               /* Moderate or Severe Liver Disease */                                                                             
               if DX(i) IN: ("K704","K711","K721","K729","K765","K766","K767","I850","I859","I864","I982")                        
                             then CC_GRP_15 = 1;                                                                                  
               LABEL CC_GRP_15 = "Moderate or Severe Liver Disease";                                                              
                                                                                                                                  
               /* Metastatic Carcinoma */                                                                                         
               if DX(i) IN: ("C77","C78","C79","C80") then CC_GRP_16 = 1;                                                         
               LABEL CC_GRP_16 = "Metastatic Carcinoma";                                                                          
                                                                                                                                  
               /* AIDS/HIV */                                                                                                     
               if DX(i) IN: ("B20","B21","B22","B24") then CC_GRP_17 = 1;                                                         
               LABEL CC_GRP_17 = "AIDS/HIV";                                                                                      
                                                                                                                                  
            %if &type=on %then end; ;                 /* end if DXTYPE(i) ^= "2" */                                               
                                                                                                                                  
          end;                   /* end do i = 1 to 25 */                                                                         
                                                                                                                                  
          /* Count total number of groups for each record */                                                                      
                                                                                                                                  
         TOT_GRP = CC_GRP_1  + CC_GRP_2  + CC_GRP_3  + CC_GRP_4  + CC_GRP_5  + CC_GRP_6  + CC_GRP_7  + CC_GRP_8  +                
                   CC_GRP_9  + CC_GRP_10 + CC_GRP_11 + CC_GRP_12 + CC_GRP_13 + CC_GRP_14 + CC_GRP_15 + CC_GRP_16 +                
                   CC_GRP_17;                                                                                                     
         LABEL TOT_GRP = "Total CCI Groups per record";                                                                           
                                                                                                                                  
          run;                                                                                                                    
                                                                                                                                  
          options notes ;                                                                                                         
           %put ;                                                                                                                 
           %put NOTE: _Charlson Finished &out created ;                                                                           
         %put ;                                                                                                                   
                                                                                                                                  
          %goto exit ;                                                                                                            
                                                                                                                                  
        %out1:                                                                                                                    
                %put ERROR: Prior Step failed with an Error submit a null data step to correct ;                                  
          %goto exit ;                                                                                                            
                                                                                                                                  
          %out2:                                                                                                                  
                %put ERROR: Input Data Was Not Defined;                                                                           
          %goto exit ;                                                                                                            
                                                                                                                                  
        %out3:                                                                                                                    
            %put ERROR: Input Data &libname..&data does not exist ;                                                               
            %goto exit ;                                                                                                          
                                                                                                                                  
        %exit:                                                                                                                    
                                                                                                                                  
         %**** Reset the SAS options ;                                                                                            
         options &opts ;                                                                                                          
                                                                                                                                  
    %mend _CharlsonICD10;                                                                                                         
                                                                                                                                  
                                                                                                                                  
