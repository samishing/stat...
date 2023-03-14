---
jupyter:
  colab:
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

<div class="cell code" id="Uu9OeFWkV-N5">

``` python
```

</div>

<div class="cell markdown" id="QId66FBoWDXv">

## Starbucks dataset background

**Description**

Dataset describing the peoople who enjoy Starbucks

**Github**:
<https://github.com/prasertcbs/basic-dataset/blob/master/Starbucks%20satisfactory%20survey.csv>

**Sample size**: 104

**Feature documentation**:

</div>

<div class="cell markdown" id="F3DSuD16aR73">

## Hypothesis

Tell us what your idea is and why you have chosen to pursue this idea.

-   I am interested in "*Do students or employees will enjoy Starbucks
    again?*"

What two groups you are comparing:

-   **G1**: Students who will enjoy Starbucks again; **G2**: Employees
    who will enjoy Starbucks again

What you will be measuring (i.e., what your response variable will be)

-   If people will enjoy Starbucks again

Is your response variable quantitative rather than categorical?

-   `If people will enjoy Starbucks again` is binary data, with the
    order `1 > 0`, which can be regarded as a quantitative variable.

Make a prediction about what kind of difference you expect to see
between your samples and WHY.

-   I'd expected that **G2**\>**G1** since employee have income

Talk about how you will gather your data

-   From Github link:
    <https://github.com/prasertcbs/basic-dataset/blob/master/Starbucks%20satisfactory%20survey.csv>

If you had unlimited resources (time, money, staff, etc.) how would you
collect your data?

-   \(i\) Collect the dataset by myself from all Starbucks; (ii)
    Investigate the most suitable sampling subset

</div>

<div class="cell markdown" id="WQHS-7kfefkY">

## Prepare your dataset

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:756}"
id="wn0v2M7maUFT" outputId="cf5b4ae3-ccb1-424a-df5a-c88a00ba40fa">

``` python
## load dataset from github 

import pandas as pd

df = pd.read_csv('https://raw.githubusercontent.com/prasertcbs/basic-dataset/master/Starbucks%20satisfactory%20survey.csv')
df.head(5)
```

<div class="output execute_result" execution_count="4">

                          Timestamp 1. Your Gender    2. Your Age  \
    0  2019/10/01 12:38:43 PM GMT+8         Female  From 20 to 29   
    1  2019/10/01 12:38:54 PM GMT+8         Female  From 20 to 29   
    2  2019/10/01 12:38:56 PM GMT+8           Male  From 20 to 29   
    3  2019/10/01 12:39:08 PM GMT+8         Female  From 20 to 29   
    4  2019/10/01 12:39:20 PM GMT+8           Male  From 20 to 29   

      3. Are you currently....? 4. What is your annual income?  \
    0                   Student             Less than RM25,000   
    1                   Student             Less than RM25,000   
    2                  Employed             Less than RM25,000   
    3                   Student             Less than RM25,000   
    4                   Student             Less than RM25,000   

      5. How often do you visit Starbucks? 6. How do you usually enjoy Starbucks?  \
    0                               Rarely                                Dine in   
    1                               Rarely                              Take away   
    2                              Monthly                                Dine in   
    3                               Rarely                              Take away   
    4                              Monthly                              Take away   

      7. How much time do you normally  spend during your visit?  \
    0                       Between 30 minutes to 1 hour           
    1                                   Below 30 minutes           
    2                       Between 30 minutes to 1 hour           
    3                                   Below 30 minutes           
    4                       Between 30 minutes to 1 hour           

      8. The nearest Starbucks's outlet to you is...?  \
    0                                      within 1km   
    1                                       1km - 3km   
    2                                   more than 3km   
    3                                   more than 3km   
    4                                       1km - 3km   

      9. Do you have Starbucks membership card?  ...  \
    0                                       Yes  ...   
    1                                       Yes  ...   
    2                                       Yes  ...   
    3                                        No  ...   
    4                                        No  ...   

      11. On average, how much would you spend at Starbucks per visit?  \
    0                                     Less than RM20                 
    1                                     Less than RM20                 
    2                                     Less than RM20                 
    3                                     Less than RM20                 
    4                                 Around RM20 - RM40                 

      12. How would you rate the quality of Starbucks compared to other brands (Coffee Bean, Old Town White Coffee..) to be:  \
    0                                                  4                                                                       
    1                                                  4                                                                       
    2                                                  4                                                                       
    3                                                  2                                                                       
    4                                                  3                                                                       

       13. How would you rate the price range at Starbucks?  \
    0                                                  3      
    1                                                  3      
    2                                                  3      
    3                                                  1      
    4                                                  3      

       14. How important are sales and promotions in your purchase decision?  \
    0                                                  5                       
    1                                                  4                       
    2                                                  4                       
    3                                                  4                       
    4                                                  4                       

       15. How would you rate the ambiance at Starbucks? (lighting, music, etc...)  \
    0                                                  5                             
    1                                                  4                             
    2                                                  4                             
    3                                                  3                             
    4                                                  2                             

       16. You rate the WiFi quality at Starbucks as..  \
    0                                                4   
    1                                                4   
    2                                                4   
    3                                                3   
    4                                                2   

       17. How would you rate the service at Starbucks? (Promptness, friendliness, etc..)  \
    0                                                  4                                    
    1                                                  5                                    
    2                                                  4                                    
    3                                                  3                                    
    4                                                  3                                    

       18. How likely you will choose Starbucks for doing business meetings or hangout with friends?  \
    0                                                  3                                               
    1                                                  2                                               
    2                                                  3                                               
    3                                                  3                                               
    4                                                  3                                               

       19. How do you come to hear of promotions at Starbucks? Check all that apply.  \
    0  Starbucks Website/Apps;Social Media;Emails;Dea...                               
    1                     Social Media;In Store displays                               
    2                       In Store displays;Billboards                               
    3                  Through friends and word of mouth                               
    4                Starbucks Website/Apps;Social Media                               

      20. Will you continue buying at Starbucks?  
    0                                        Yes  
    1                                        Yes  
    2                                        Yes  
    3                                         No  
    4                                        Yes  

    [5 rows x 21 columns]

</div>

</div>

<div class="cell markdown" id="5qlEQxR-f1U1">

Tell us what groups you want to compare in the dataset

-   **G1** (buy starbuck \| occupation=student) vs. **G2** (buy starbuck
    \| non-student)

</div>

<div class="cell markdown" id="cWTNiVgdhiDn">

-   Print first 5 records of each group, respectively.

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="ucJCzSRXh_E6" outputId="5e4cc513-9233-4e3c-840f-1d85759c97b1">

``` python
## First 5 records of G1 (student)
(df[df['3. Are you currently....?'] == 'Student']['20. Will you continue buying at Starbucks?']).head(5)
```

<div class="output execute_result" execution_count="12">

    0    Yes
    1    Yes
    3     No
    4    Yes
    5    Yes
    Name: 20. Will you continue buying at Starbucks?, dtype: object

</div>

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="YXoXo_5tlUvJ" outputId="469eeb32-7efe-4735-8e1c-3c22d1d7ed23">

``` python
## First 5 records of G2 (employed)
(df[df['3. Are you currently....?'] == 'Employed']['20. Will you continue buying at Starbucks?']).head(5)
```

<div class="output execute_result" execution_count="28">

    2     Yes
    7     Yes
    9     Yes
    15     No
    16    Yes
    Name: 20. Will you continue buying at Starbucks?, dtype: object

</div>

</div>
