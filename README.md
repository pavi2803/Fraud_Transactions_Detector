# Fraud_Transactions_Detector
This project focuses on detecting fraudulent transactions from the BankSim Dataset.

### Project Summary
Financial transaction security remains a critical concern for credit card companies and financial institutions. Accurately identifying whether a transaction is legitimate is not only essential for customer trust but also a significant cost-saving measure. In fact, CNBC reported that over $16 billion was lost to fraudulent transactions in 2016 alone.

### Objective
Can we leverage historical transaction data to accurately determine whether a given transaction is fraudulent or legitimate?

### Dataset Overview
We utilized a dataset sourced from Kaggle, consisting of 594,643 transaction records, with 587,443 labeled as genuine and 7,200 as fraudulent. The data is synthetically generated using the BankSim transaction simulation tool and includes 10 features such as customer demographics, merchant information, and transaction amount.

### Data Preprocessing
To prepare the data for modeling:

All columns were initially strings wrapped with apostrophes — we removed these.

Columns were converted to appropriate data types: most features are categorical, except for the amount field.

ZIP code fields (for both customer and merchant) were dropped, as each contained only a single unique value.

We applied pandas.get_dummies() to convert categorical features into binary indicator variables for model compatibility.

### Model Evaluation
Model	Precision	Recall	False Positives (FP)	False Negatives (FN)
Naive Bayes	0.1957	0.9993	2	11,695
Logistic Regression	0.8887	0.7236	796	261
Neural Network	0.8721	0.7624	684	322
Decision Tree	0.9027	0.7212	803	224
Random Forest	0.8845	0.7462	1,096	421

### Insights & Conclusion
While Naive Bayes yields the highest recall and lowest number of false positives, its precision is extremely low, meaning it flags many non-fraudulent transactions. Despite this, the cost of a false negative (missed fraud) is more severe than a false positive (an extra verification step), making its low FN rate valuable.

However, the Neural Network model stands out with a strong balance — high precision, competitive recall, and the second-lowest FP rate — making it highly effective for fraud detection.

Overall, based on our results, the Neural Network and Naive Bayes models offer the best trade-offs for identifying fraudulent transactions accurately.
