# Customer Satisfaction Prediction (Machine Learning Project)

## Overview

This project applies multiple machine learning models to predict **customer satisfaction scores** using behavioral and interaction data.

The project explores two main questions:

1. Which model best predicts customer satisfaction?
2. Which customer behavior variables are most important in predicting satisfaction?

To answer these questions, several models were implemented, including both **custom-built algorithms** and **library-based machine learning models**.

---

## Dataset

The dataset used is the **Customer Experience Dataset** from Kaggle.

It contains **1000 customer observations** and several variables describing user interactions, behavior, and satisfaction.

In this project, the following variables are used.

### Independent Variables (Features)

- Num_Interactions
- Feedback_Score
- Products_Purchased
- Products_Viewed
- Time_Spent_on_Site

### Dependent Variable (Target)

- Satisfaction_Score

The goal is to predict **Satisfaction_Score** using these five behavioral features.

---

## Data Preprocessing

### Missing Values

Missing values are handled by filling them with the **column mean**.

### Train/Test Split

The dataset is split into:

- 70% training data
- 30% testing data

### Feature Normalization

Z-score normalization is applied:

X_normalized = (X - mean) / std

The mean and standard deviation are calculated **only from the training data** and then applied to both training and test datasets.

---

## Models Implemented

Five models are implemented and compared.

### 1. Linear Regression (From Scratch)

A multivariate linear regression model implemented manually using **gradient descent**.

The model iteratively updates parameters until the loss improvement falls below a threshold.

This model serves as a **baseline model**.

---

### 2. K-Nearest Neighbors Regression (From Scratch)

A custom implementation of **KNN regression**.

Steps:

1. Compute Euclidean distance between test and training samples
2. Select the k nearest neighbors
3. Predict using the average of their target values

In this project:

k = 3

---

### 3. Polynomial Regression

Polynomial regression implemented using **Scikit-learn**.

PolynomialFeatures with degree 2 is used to allow the model to capture **nonlinear relationships** between variables.

---

### 4. Decision Tree (From Scratch)

A regression decision tree implemented manually.

The splitting rule is based on **variance reduction**, where the algorithm selects the feature and threshold that reduce the variance of the target variable the most.

This model is also used to compute **feature importance**.

---

### 5. XGBoost Regression

A gradient boosting model implemented using **XGBoost**.

Key parameters include:

- n_estimators = 500
- learning_rate = 0.03
- max_depth = 3
- subsample = 0.8
- colsample_bytree = 0.8

XGBoost is used both for **prediction performance comparison** and **feature importance analysis**.

---

## Model Evaluation

Model performance is evaluated using **Root Mean Squared Error (RMSE)**.

RMSE = sqrt(mean((y - y_hat)^2))

Lower RMSE indicates better prediction performance.

Both **training RMSE** and **testing RMSE** are compared for all models.

---

## Results

### Model Performance

The results show that:

- Linear Regression performs best on the test dataset
- Polynomial Regression performs similarly but slightly worse
- KNN shows some overfitting behavior
- Decision Tree performs moderately
- XGBoost provides competitive predictive performance

---

## Feature Importance

Feature importance is evaluated using two tree-based models:

- Decision Tree
- XGBoost

Both models suggest that the most important predictor of customer satisfaction is:

Time_S
