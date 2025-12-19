# Performing Linear Regression in Keras – Bike Demand Prediction

## Overview
This project implements linear regression models using Keras to analyze and predict demand for shared bikes in a city. The work was completed as part of the **IBM SkillShare / Skills Network lab: “Performing Linear Regression in Keras”**, where the objective is to understand which environmental and temporal factors most influence bike rental demand.

The analysis compares single-variable and multi-variable linear regression models and evaluates their predictive performance using Root Mean Squared Error (RMSE).

---

## Business Context
During the COVID-19 pandemic, a bike-sharing service experienced a significant drop in revenue. As part of the analytics process, understanding the factors that drive bike demand is a critical first step toward designing a recovery strategy.

This lab focuses on:
- Identifying demand drivers
- Quantifying feature impact
- Evaluating prediction accuracy using regression models

---

## Dataset
**Bike Sharing Dataset (UCI Machine Learning Repository)**

- **Target Variable:** `cnt` – total number of rental bikes
- **Features Used:**
  - Season, year, month, weekday, working day
  - Holiday indicator
  - Weather situation
  - Temperature (`temp`), perceived temperature (`atemp`)
  - Humidity (`hum`)
  - Windspeed (`windspeed`)

**Dropped Columns (to prevent data leakage or redundancy):**
- `instant`, `dteday`
- `casual`, `registered`

---

## Objectives
- Build linear regression models using Keras
- Predict a continuous target variable
- Compare single-input vs multi-input regression
- Apply feature normalization for stable training
- Interpret learned model weights

---

## Data Preparation & Exploration
- Removed non-numeric and leakage-prone columns
- Performed bivariate and multivariate analysis
- Visualized relationships using:
  - Scatter plots
  - Box plots
  - Pair plots
  - Correlation heatmaps

**Key EDA Findings:**
- Positive correlation: `temp`, `atemp`, `yr` → `cnt`
- Negative correlation: `hum`, `windspeed`, `weathersit`, `holiday` → `cnt`
- Highest demand observed in Fall and during clear weather
- Demand increased year-over-year

---

## Model 1: Single-Variable Linear Regression
**Input Feature:** `temp`  
**Architecture:**
- Normalization layer
- Dense layer (1 unit)

**Training:**
- Optimizer: SGD (learning rate = 0.001)
- Epochs: 100

### Result
- **Test RMSE:** **1437.10**

**Insight:**  
Temperature alone explains general demand trends but lacks sufficient predictive power.

---

## Model 2: Multi-Variable Linear Regression
**Input Features:** All numerical features  
**Architecture:**
- Normalization layer
- Dense layer (1 unit)

**Training:**
- Optimizer: SGD (learning rate = 0.001)
- Epochs: 100

### Result
- **Test RMSE:** **902.31**

**Insight:**  
Including multiple features significantly improves prediction accuracy by capturing interactions between weather, time, and seasonal variables.

---

## Feature Importance (Model Weights)
The learned weights confirm insights from exploratory analysis:

- Strong positive contributors:
  - `yr`
  - `temp`
  - `atemp`
- Strong negative contributors:
  - `weathersit`
  - `hum`
  - `windspeed`
  - `holiday`

This alignment validates both the data exploration and the regression model.

---

## Neural Network for Linear Regression (Additional Exercise)
**Dataset:** Iowa Housing  
**Target:** `SalePrice`  
**Feature:** `SquareFeet`

**Architecture:**
- Dense hidden layer (ReLU, 500 units)
- Dense output layer

**Training:**
- Optimizer: Adam
- Epochs: 30

**Result:**  
The neural network successfully learned the linear trend and produced reasonable predictions on unseen test data.

---

## Auto MPG Regression (Exercise)
**Dataset:** Auto MPG (UCI)  
**Target:** `MPG`

### Result
- **Test RMSE:** **6.05**

This exercise reinforces multi-variable regression with normalization on a classic benchmark dataset.

---

## Technologies Used
- Python
- TensorFlow / Keras
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn

---

## Learning Context
This project was completed as part of the **IBM SkillShare / Skills Network – Performing Linear Regression in Keras** lab and is intended as a hands-on learning exercise in regression modeling, feature analysis, and evaluation.

---

## Completion
**Completed by Qazi Fabia Hoq**  
*(Exercise-based lab for IBM SkillShare / Skills Network)*

---

© IBM Corporation (Original lab content). All rights reserved.
