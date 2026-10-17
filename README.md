# Ambulance Demand Prediction Using Machine Learning 🚑

## About the Project

This project focuses on analyzing emergency medical service (EMS) calls and identifying periods when ambulance demand is likely to be high.

The idea was to understand how emergency call patterns change over time and whether machine learning can help identify high-demand hours using historical call data, time-based patterns, and additional features.

I worked on building a complete workflow that includes data preparation, feature engineering, model training, evaluation, and visualizations to better understand ambulance demand.

## Problem Statement

How can historical emergency call data be used to identify hours with high ambulance demand?

## Dataset

The project uses the 911 emergency calls dataset, containing 99,492 records and 9 original columns.

The data includes timestamps, locations, incident descriptions, and emergency call categories. I focused on EMS-related calls and aggregated them into hourly demand counts.

The notebook also creates additional demonstration features for weather, traffic, population density, and hospital availability.

**Important:** These additional features are synthetically generated or estimated proxies, not verified real-world measurements. They are used to demonstrate feature engineering and should not be interpreted as actual weather, traffic, population, or hospital data.

## What I Worked On

### 1. Data Preparation

I loaded the emergency call dataset, converted timestamps into a usable datetime format, handled invalid timestamps, and prepared the data for analysis.

### 2. Feature Engineering

I extracted information such as hour of the day, day of the week, month, and weekend status.

I also created lag features, rolling averages, and cyclical time encodings to represent patterns in ambulance demand.

### 3. Hourly Demand Analysis

I aggregated EMS calls into hourly counts and explored patterns in demand across different hours and days.

The visualizations include an hourly-versus-weekday heatmap and a comparison between actual high-demand hours and the hours predicted by the model.

### 4. Machine Learning Models

I used a voting ensemble combining:

- XGBoost
- Random Forest
- Logistic Regression

The ensemble combines predictions from multiple models to classify each hour as high demand or not high demand.

### 5. Model Evaluation

I evaluated the model using accuracy, precision, recall, F1-score, a classification report, and a confusion matrix.

I also experimented with different smoothing windows and quantile thresholds to define high-demand periods.

## Results

The selected configuration in the notebook uses a three-hour smoothing window and a 60th-percentile threshold.

| Metric | Result |
|---|---:|
| Accuracy | 92.84% |
| Precision | 90.22% |
| Recall | 93.49% |
| F1-score | 91.83% |

These metrics describe the selected model's performance on the notebook's time-ordered test split. They should be interpreted in the context of the chosen demand threshold and the synthetic demonstration features.

## Technologies Used

- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- scikit-learn
- XGBoost
- imbalanced-learn

## How to Run the Project

The notebook is designed for Google Colab.

1. Open the notebook in Google Colab.
2. Run the installation and import cells.
3. Upload the original `911.csv.zip` file when prompted.
4. Run the data enrichment section to create `911_enriched.csv`.
5. Upload the enriched CSV when prompted by the modeling pipeline.
6. Run the remaining cells to train the models and generate the visualizations.

The original dataset and the generated enriched CSV are not included by default. You will need to provide the input dataset to reproduce the analysis.

## What I Learned

This project helped me understand how time-based patterns can be used in a machine learning problem. I learned how to aggregate event data, create lag and rolling features, compare multiple models, and evaluate a classifier using more than just accuracy.

It also helped me understand the importance of being transparent about synthetic features and the limitations of a model when applying it to a real-world problem.

## Limitations and Future Scope

The additional weather, traffic, population-density, and hospital-count features are synthetic or proxy-based, so the results should not be treated as evidence of real-world ambulance demand forecasting performance.

In the future, I would like to integrate verified external data sources, test the model on later unseen time periods, and explore demand forecasting methods that could support emergency service planning.

---

This project was a hands-on learning experience in time-based data analysis, feature engineering, and machine learning for a real-world-inspired problem.
