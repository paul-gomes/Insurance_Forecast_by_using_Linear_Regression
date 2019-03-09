
# Insurance Forecast by using Linear Regression

### Project Description

This is a linear regression project, where I will use data to create a model that has a single numerical output. For the first part of the project - prediction - I have chosen a insurance cost datasets from kaggle. 

### Goal
My goal here is to predict the insurace cost based on different parameters. 

### Dataset link
https://www.kaggle.com/mirichoi0218/insurance

### Initial Exploration 

Dataset has 7 feature - 'age', 'sex', 'bmi', 'children', 'smoker', 'region', 'charges'. 
1. age         1338 non-null int64
2. sex         1338 non-null object
3. bmi         1338 non-null float64
4. children    1338 non-null int64
5. smoker      1338 non-null object
6. region      1338 non-null object
7. charges     1338 non-null float64

#### Correlation 

|  | age | bmi | children | charges | isSmoker | region_num |
|------------|-----------|-----------|-----------|----------|-----------|------------|
| age | 1.000000 | 0.109272 | 0.042469 | 0.299008 | -0.025019 | -0.002127 |
| bmi | 0.109272 | 1.000000 | 0.012759 | 0.198341 | 0.003750 | -0.157566 |
| children | 0.042469 | 0.012759 | 1.000000 | 0.067998 | 0.007673 | -0.016569 |
| charges | 0.299008 | 0.198341 | 0.067998 | 1.000000 | 0.787251 | 0.006208 |
| isSmoker | -0.025019 | 0.003750 | 0.007673 | 0.787251 | 1.000000 | 0.002181 |
| region_num | -0.002127 | -0.157566 | -0.016569 | 0.006208 | 0.002181 | 1.000000 |

![Correlation](/images/correlation.PNG)

It looks like all of the featuers are important for forcasting the insurance costs. However, some of the important features - 'smoker', 'region' is in object. As a result, I had to convert them to numerical values before I can feed them into the model. There are no missing values and all the features seem important for the prediction. So, I would not be needing any cleaning here. After analyzing the dataset, It looks like there is strong correlation between 'isSmoke' and 'charges', which is .787, a strong positive correlation. There is also correlation between 'age' and the 'charges', which is .299, a weak positive correlation. 

### Linear Regression
1. Initial set of features for X : isSmoker(which is a new feature that coverts smoker feature into numerical values(0,1)), age 
2. Initial set of features for Y: charges

I want predict individual insurance cost. 'isSmoke' and 'age' are an important factors here that could affect someone's insurance cost. As a result, I would choose 'iSmoke' and 'age' as my parameters for my model at first. Later, I would see if 'bmi' and 'region' help make the model better.

#### Findings
1. The score is  0.7155021764803258
2. mean squared error is  41750283.75412038
3. The root mean squared error is  6461.445949175802

The score here is pretty good, 0.71550. As we know, the closer to 1 the score is the better the model. However, we can definitly improve the model by adding more important parameters. The initial parameters are 'isSmoke' and 'age' and I intend to improve the model by adding 'bmi', 'region_num'. The mean squared error is 41750283.7541, which is too much. The smaller the means squared error, the closer you are to finding the line of best fit. However, it is very difficult to get a small mean squared error.

#### Attempt to improve the model

1. Set of features for X : isSmoker(which is a new feature that coverts smoker feature into numerical values), age, bmi, region_num(new created numerical feature for region) 
2. Set of features for Y: charges

#### Findings
1. The score on the train_set is  0.7413490482280484

It seems like adding 'bmi', 'region_num' improves the model, and brings the score to 0.741449, which is better than the previous one. After my analysis, it is safe to say that 'isSmoker', 'age', 'bmi', 'region' affects the insurace cost very much. 

#### Result on test datasets
1. The score on test_set is  0.772722801913057

The score on test dataset is higher. One of interesting findings here is that, if you smoke, your insurace costs tend to be higher. Moreover, smoking damages our body's natural defenses against the bacteria and viruses that cause pneumonia, which is my next project, classifying pneumonia from chest X-Ray images.


