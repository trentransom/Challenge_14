# Stats
## Original Strategy
Short Window: 4 periods
Long Window: 100 periods
Training Period: 3 months

                precision    recall  f1-score   support

        -1.0       0.43      0.04      0.07      1804
         1.0       0.56      0.96      0.71      2288

    accuracy                           0.55      4092
   macro avg       0.49      0.50      0.39      4092
weighted avg       0.50      0.55      0.43      4092

## 2 Month Training Period
Short Window: 4 periods
Long Window: 100 periods
Training Period: 2 months

                precision    recall  f1-score   support

        -1.0       0.39      0.04      0.06      1825
         1.0       0.56      0.96      0.70      2318

    accuracy                           0.55      4143
   macro avg       0.47      0.50      0.38      4143
weighted avg       0.48      0.55      0.42      4143

## 6 Month Training Period
Short Window: 4 periods
Long Window: 100 periods
Training Period: 6 months

                precision    recall  f1-score   support

        -1.0       0.44      0.02      0.04      1732
         1.0       0.56      0.98      0.71      2211

    accuracy                           0.56      3943
   macro avg       0.50      0.50      0.38      3943
weighted avg       0.51      0.56      0.42      3943 

## Short Window Strategy
Short Window: 2 periods
Long Window: 25 periods
Training Period: 3 months

                precision    recall  f1-score   support

        -1.0       0.40      0.08      0.13      1828
         1.0       0.56      0.91      0.69      2324

    accuracy                           0.54      4152
   macro avg       0.48      0.49      0.41      4152
weighted avg       0.49      0.54      0.44      4152

## Combo Strategy
Short Window: 3 periods
Long Window: 100 periods
Training Period: 24 months
                
                precision    recall  f1-score   support

        -1.0       0.70      0.01      0.01      1229
         1.0       0.56      1.00      0.72      1565

    accuracy                           0.56      2794
   macro avg       0.63      0.50      0.36      2794
weighted avg       0.62      0.56      0.41      2794

## ADA Boost Strategy
Short Window: 4 periods
Long Window: 100 periods
Training Period: 3 months
Model: ADA Boost model

                precision    recall  f1-score   support

        -1.0       0.44      0.33      0.37      1804
         1.0       0.56      0.67      0.61      2288

    accuracy                           0.52      4092
   macro avg       0.50      0.50      0.49      4092
weighted avg       0.50      0.52      0.50      4092


## Summary
The original strategy slightly outperformed the index fund as you can see in the plot here. 
![First Strategy Plot](https://raw.githubusercontent.com/trentransom/Challenge_14/main/Plots/first_strategy_returns.png)

Over the period of the testing data, the index fund gets about a 40% return and the trading strategy gets a 50% return.

When attempting to optimize the model we tried changing the length of the training data. We tried with a 2 month period and a 6 month period. 
Shown below is the plot of the strategy with a 2 month training period.
![2 Month Training](https://raw.githubusercontent.com/trentransom/Challenge_14/main/Plots/2_month_train_returns.png)
Shown below is the plot of the strategy with a 6 month training period.
![6 Month Training](https://raw.githubusercontent.com/trentransom/Challenge_14/main/Plots/6_month_train_returns.png)

As you can see, lengthening the training data greatly improved the performance of the model and shortening it made the performance worse. At the end of the testing data period the strategy with 6 months training data had a return of over 80%. 

The next strategy we attempted to optimize the model is to change the length of the SMA windows. We tried a short window of 2 and long window of 25. I also tried lengthening the SMA windows but this always had much worse results. 
Seen below is the plot of the returns for the shorter window SMA strategy.
![Shorter SMA](https://raw.githubusercontent.com/trentransom/Challenge_14/main/Plots/2_short_25_long.png)

This model has suboptimal performance. During a large portion of the testing data the model is underperforming the mutual fund and at the end the return is nearly identical. 

My best performing model was with a 24 month period of training data. Seen below is the plot of this strategy's returns.
![24 Month Train](https://raw.githubusercontent.com/trentransom/Challenge_14/main/Plots/24_month_train_3_short_100_long.png)

This model never underperforms the index fund and by the end of the testing data has outperformed it. It has about the same return as the strategy with the 6 month training period but here the testing data is 18 months shorter so the rate of return is much better. 

Finally I tried using the AdaBoost model. This model learns to assign higher weight to instances in the data which are more difficult to assign correctly. With this model we used the same strategy as the original model. 
Below is the chart of the performance of that model. 
![AdaBoost Model](https://raw.githubusercontent.com/trentransom/Challenge_14/main/Plots/ada_returns.png)

Tinkering with this model I could not get it to perform better than the SVM models. It is able to achieve much higher recall for the -1 class but the performance is subpar. 

Overall The best model was the model trained on 24 months of data. It achieved the highest returns of any model in a shorter time. 




