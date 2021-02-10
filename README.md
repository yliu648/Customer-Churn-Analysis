# Customer-Churn-Analysis - Churn Classification Model

This code aims to predict customer churn based on order history (SKUs & volume), order frequency, location of order, customer type, and customer experience. 

## Independent variables generated by feature engineering

<img src="Features engineering for churn model.jpg" width="70%">

## Dependent Variable 
Labeling churn for non-contractual business was a major challenge. Our team tried a number of approaches to label churn, and the final approach that showed the highest accuracy was to use the 12-month threshold for labeling churn while using 6-month for non-churn. The six-month threshold is an industry-wide standard and the 75th percentile of average purchase interval, while the 12-month threshold is the 94th percentile. Using the 12-month threshold, instead of 6-month, to label churn reduces the number of non-churn customers incorrectly labelled as churn.

<img src="Approach for labeling churn.png" width="80%">

## Model Selection and Evaluation
We applied three different classification models to predict customer churn. We chose logistic regression as the baseline model since it is a linear classifier for binary classes and the coefficients of features generate insights on the linear association with churn. Random forest and extreme gradient boosting were used as the advanced prediction models because ensemble tree-based models usually perform better than individual classifiers by reducing the individual errors of trees. Random forest may give a more consistent result, but the performance may not be so high since not every tree model utilizes all the data. Xgboost is a more efficient algorithm for large dataset and prioritizes performance while reducing overfitting.
 
<img src="Confusion matrix of three models.png" width="80%">

<img src="Evaluation of three models.png" width="80%">
Extreme Gradient Boosting performed the best in terms of highest accuracy for testing data, precision, and recall measures. 


## Model Results and Insights
 
<img src="Top 10 Features by XgBoost & Coefficients by Logistic Reg.png" width="80%">

Figure 5 and 6 showed that customers buying knit tops, T-shirts, and woven tops are unlikely to churn since the coefficients are negative. In terms of distribution channel, customers who order products from store 18 or products shipped through the retail channel are less likely to churn. It’s interesting that customers who place large orders tend to churn. This might be because customers placing orders with larger qty tend to purchase less frequently. 
 
<img src="Customer Churn Distribution.png" width="70%">

Figure 7 showed the distribution of customer churn. The first pie chart on the top left corner revealed that about 1% customers may only be given promotions but no sales transactions in recent two years. For the real customers with valid purchase histories, the overall churn rate is about 59%, which seems relatively high for a retail business. More than half of the churn customers had no purchase in the recent year. The churn rate for new customers is as high as 92%, while that for established customers is only 53%.

<img src="customer mapping.jpg" width="60%">

Figure 8 is a quadrant diagram mapping quantity and profit per order for the predefined customer groups. Customers in the groups Young City Solos, Pastoral Pride, and Cultural Connections are valuable as they tend to place large orders in terms of quantity and profit. However, they all have relatively high churn rates. 

Figure 9 showed that customers who made higher sales per order tend to have a higher proportion of sales return, such as Young City Solos and Cultural Connections, but except for Pastoral Pride who made higher sales but lower proportion of returns. Power Elite group also has higher sales but is unlikely to churn so it is acceptable for them to have higher return rates. Therefore, we suggest targeting the three valuable customer groups by giving promotions to encourage frequent purchases and improve the churn rate.
