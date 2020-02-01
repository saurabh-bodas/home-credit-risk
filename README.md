# Credit Risk Evaluation
### Is a client with limited credit history capable of repaying a loan?

Founded in the Czech Republic, Home Credit strives to offer loans to individuals with limited/non-existent credit history. Using information about income, family size, type of house, employment, and other transaction history, a client's repayment capacity is determined.

## The Data

Home Credit provided data about its clients through a Kaggle compeition. We used Python and PySpark on the databricks platform for model building and evaluation, while Tableau was used for data visualisation. 

We analysed the impact of gender, age, income, education level, house ownership of Home Credit's customers on whether they defaulted on their payments. 

Note: 1 represents that the individual defaulted on the loan

## Model building & evaluation



Following extensive exploratory data analysis and visualization, the following models were deployed: 

i. Logistic regression (AUC score: 0.68)

ii. Catboost (AUC score: 0.55)

iii. Random Forest (AUC score: 0.65)

iv. Random Forest with SMOTE resampling method (AUC score: 0.63)

Because the dataset was expectedly highly imbalanced (8% positive/defaulters), SMOTE resampling was tried out, but did not yield favourable results. The Area Under the Receiver Operating Characteristic curve (AU-ROC score) was the primary metric used for evaluation. 

The AUROC score was used instead of the confusion matrix because the data is highly imbalanced - the confusion matrix would report a high enough accuracy (>80%) simply due to the nature of the data (i.e. most individuals do not default). 

Another important point is that false negatives (i.e. classifying loan defaulters as non-defaulters and extending them credit) are the most dangerous (expensive to the company) and care should be taken to avoid them at all times. Thus, a more conservative estimate was set for these models to classify them as potential defaulters.

## Model selection

Logistic regression was determined to be the most important model because: 

i. shorter training time (especially since we had a large dataset and limited processing power)

ii. interpretability (provides feature importance and the direction of features i.e. positive/negative)

iv. provides us with reliable estimates of conditional probabilities compared to random forests

## Conclusion

Feature engineering on more variables, better management of missing data, dimensionality reduction, and more complex models like the XGBoost and neural networks could be implemented to further improve model performance (limited resources of the Databricks community edition inhibited our efforts). 





