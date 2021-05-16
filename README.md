# Capstone-Software-Operational-Anomaly-Detection
Objective:
Given an IT department’s operational data for multiple software machines, identify features that contribute the most to run time anomalies so as to investigate potential failures and prevent downtimes before they happen.

Result:
The most important features that contribute to anomaly detection are:
1.	System CPU 
2.	Last GC duration: Marksweep
3.	Memory space usage: PS Eden Space used
4.	Connection delay: source08 CPR

Dataset:
The data is taken from Kaggle and consists of 200 datasets representing separate software machines. We looked at machine 67.

Constraints:
•	Data only available for 1-month span
•	Subject matter expertise required to understand features
•	Potentially many highly correlated features

Model:
After comparing auc-roc curve of mutiple classification models, we decided to use XGBoost.
We used GridSearchCV for hyperparameter tuning and obtained: 
•	roc_auc = 0.88
•	F1 score = 0.86


Feature Aggregation:
We calculated 95th percentile of each of the four features from the training set to calculate the thresholds:
•	System CPU - 0.19
•	Last GC duration: Marksweep	- 1897
•	Memory space usage: PS Eden Space used	- 0.56
•	Connection delay: source08 CPR - 61

Recommendation:
To minimize future failures, we recommend implementation of an alert mechanism to be implemented that notifies stakeholders as soon as the cutoff limit of any of the 4 most important features is reached. The stakeholders can then troubleshoot to determine the underlying cause and prevent operational failures.  
