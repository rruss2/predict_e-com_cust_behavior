# Predicting E-Commerce Customer Behavior

## Background 
Every day there are more and more companies selling their products online versus in brick-and-mortar stores.  These companies collect data on their customers' behavior purchasing products and services online.  This data is very valuable to companies.  They analyze this data to acquire insights on their customers' buying behavior patterns.  The analysis will provide leverage to the company by creating new strategies to market customers.  In this project, I will use e-commerce data provided by a company in Turkey to predict the buying patterns of customers.  

## Objective
I will use machine learning to create a predictive model.  This model will use customers' attributes to predict whether a visitor/customer will make a purchase or not.  This model can be used for a e-commerce website to trigger a recommendation system to provide a visitor product recommendation based on the model's prediction this visitor will purchase something.

## Learning
I want to challenge myself in learning how to host and deploy a machine learning model in Google Cloud Platform (GCP).  I also wanted to learn how to write a simple Flask web application using the model I build in this project to predict whether a customer will purchase a product or not.  In addition to GCP and Flask, I wanted to learn how build machine learning pipelines to help automate the model selection process.

## Dataset
The dataset comes from a Turkey e-commerce company www.gozalangroup.com.tr/.  I extracted the data from https://www.kaggle.com/roshansharma/online-shoppers-intention named Online Shopper's Intention.

The dataset consists of 12,330 customer sessions (rows), 10 numerical and 8 categorical variables (columns). I will use ‘Revenue’ (True or False) variable as my target variable. The other 17 variables will be my predictor variables, customer's attributes, or features. I will engineer more attributes before modeling. This dataset was formed in a one-year period not including holidays, special days, or specific campaigns. The size of the data set is adequate for the data science tasks I plan on performing on it.

## Research Questions
- What are the relative important customer attributes that contribute to a customers' decision to purchase an item?
- Will a customer purchase a product or not on a e-commerce website?

## Insights from EDA

![](images/Rev_Exit.PNG)    

This violin plot shows customers that purchase a product is not on the website as long as those that do not purchase an item.  This indicates people who purchase an item generally have an idea what they want, so they do not need to shop on the website as long.  Those customers who are not sure what they want and are shopping to gather information stay on the website longer and do not purchase.  The company can consider strategies to help customers make a decision to purchase through incentives.

![](images/Dist_Months.PNG)

The bar graph shows the distributions of the months customers are active and inactive on the website.  We can see the months customers are on the website longest are May and November.  In May, people are shopping for items for summer vacations and summer season.  In November, people are shopping to purchase items for the holidays.  This is valuable information for the company to use in creating marketing campaigns.

## Feature Selection and Engineering
Multicollinearity existed among the numeric variables.  I corrected for this by dropping the following variables: ProductRelated and ExitRates.  I used one hot encoding to create new dummy variables for the categorical variables.

## Data Preprocessing
The numerical variables have outliers and skewd distributions.  I correct for this by normalizing the variables through scaling the numerical variables with StandardScaler in scikit learn.  I encoded the categorical variables with OneHotEncoder in scikit learn.  I created a preprocessing pipeline in scikit learn to automate the process.  In addition to scaling and encoding the data, I split the data into 80% training and 20% testing.

## Model Selection
Since I am predicting a true or false value for revenue, I considered several classification machine learning models.  The following models I considered were Logistic Regression, Support Vector Classifier, Decision Tree Classifier, Random Forest Classifier, Gradient Boosting Classifier, Extreme Gradient Boosting Classifier, Light Gradient Boosting Machine Classifier, and Multi-layer Perceptron Classifier.  I used a machine learning pipeline from scikit learn to display the confusion, accuracy, and classification report for each classifier.  In selecting the model, I used the F1 measure because it is a harmonic mean between precision and recall.  F1 measure accounts for an imbalance in classes of the target variable.  Through this process, I noticed Gradient Boosting Classifier algorithm performed better than all the others with 0.81 macro average.

## Relative Important Features
The top 3 relative important features in predicting purchasing behavior are shopping on the weekend, vistor type, and traffic type.  The various classes within each of these variables have higher importance.  For example, a new visitor in visitor type and traffic type 8 have significant relative importance to predicting whether a customer will purchase or not.

## Further Investigation
I want to investigate how I can use various types of neural networks to predict purchasing behavior.  I am curious about how to incorporate this model into a platform to help companies improve their purchases online.  I want to create an interface for someone to input different customer attributes to see whether that customer will purchase or not.
