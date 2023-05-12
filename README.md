# Chicago-Airbnb-Exploration

# Abstract

This analysis attempts to explore the features and drivers of Airbnb daily prices and monthly availability. As the economy continues to redefine its new post-COVID norm, Airbnb arbitrage and investment ideas have flooded the internet. The search term “Airbnb” has hit a new all time high interest in the summer of 2022 and “Airbnb Arbitrage” reaching highs towards the end of 2022. To obtain a better idea of what features are driving pricing decisions (supplier) and availability (buyer) of listing, the study uses clustering do identify groups of listings, geographic data, review information, host information, and property features.

Chicago Airbnb listing data was extracted from Inside Airbnb (last pulled 12/20/22). Natural Language Processing and K-Means clustering were used in conjunction to extract data from free form text fields and identify groups of properties with similar amenities, neighborhood description, and property features. Additionally, the report includes the methods behind cleaning outlier price data, and the various one-hot encoding and dummy variables to prepare the dataset for statistical analysis and machine learning application. 


Total accommodation is the strongest positively correlated feature with nightly price in both listings with reviews and without reviews, .52 and .33, respectively. Having a shared bathroom is the strongest negatively correlated feature with nightly price, -.42 and -.35, for listings with reviews and without reviews, respectively. For listings without reviews, the total listings under the host becomes very important. Total listings is -.47 correlated with monthly availability for listings without reviews, but drops out of importance when a listing has reviews.


# Introduction

As some listings have not had any reviews up until the time of pulling data, I have split the dataset and analysis after cleaning and performing appropriate feature engineering. I analyze the correlations and statistical significance behind some of the drivers behind price and availability. The report concludes with machine learning algorithms and deep learning models to predict nightly price and monthly availability.

# Table of Contents:
- Data Preparation: Cleaning, processing, and feature engineering
- Analysis With Reviews: Statistical analysis of listing with reviews
- Analysis Without Reviews: Statistical analysis of listings without reviews
- With Reviews - Availability Modeling: Machine learning applications to predict monthly availability of listings with reviews
- With Reviews - Price Modeling: Machine learning applications to predict nightly price of listing swith reviews
- Without Reviews - Availability Modeling: Machine learning applications to predict monthly availability of listings without reviews
- Without Reviews - Price Modeling: Machine learning applications to predict nightly price of listings without reviews

# Other Observations and Findings:

Please read the full report for further insights about the observations and findings.

- Listings with reviews that can accommodate  2, 4, and 10 have the steepest negative slope when comparing miles away from Lincoln Park and nightly price. This is similar to listings without reviews where listings that accommodate 2, 3, and 4 have strong negative slopes.
- The correlation between amount of beds and nightly price, while positively correlated (.45, .23 for listings with reviews and without reviews, respectively), flattens out after 5 beds.
- A similar effect is observable in bedrooms, where while positively correlated with price (.49, .28 for listing with reviews and without reviews, respectively), flattens out after 5-6 bedrooms.
- There does not seem to be strong positive relationships with monthly availability for listings with reviews. The top positively correlated factor has a correlation of .13. There appears to be a weak positive correlation with hosts verified using emails and phones, and accommodation with monthly availability for listings without reviews. This is understandable as listings that have no reviews and a lot of accommodations may not be popular booking options.
- Listings with reviews do not have strong negatively correlated features with monthly availability either. The strongest negative correlation is -.12.



# Model Evaluations:

With Reviews - Price

- The simple linear regression model performed relatively well. EV of .41, MAE of 48, RMSE of 68, RMAE of .35, and a Relative RMSE of .49.
- The Random Forest regressor model performed better with an EV of .55, MAE of 42, RMSE of 59, RMAE of .30, and a Relative RMSE of .43.
- The Deep Learning model performed well, however, did not yield improvement over the random forest regressor. The model using early stopping had an EV of .54, MAE of 42, RMSE of 60, RMAE of .30, and a Relative RMSE of .43.

With Reviews - Availability

- The simple linear regression model performed poorly. EV of .04, MAE of 6, RMSE of 8, RMAE of .35, and a Relative RMSE of .43.
- The Random Forest regressor model performed better with an EV of .23, MAE of 6, RMSE of 7, RMAE of .31, and a Relative RMSE of .39.
- The Deep Learning model performed poorly. The model using best only had an EV of .07, MAE of 6, RMSE of 8, RMAE of .33, and a Relative RMSE of .43.

Without Reviews - Price

- The simple linear regression model performed moderately well, notable improvement in relative RMSE and RMAE. EV of .35, MAE of 42, RMSE of 62, RMAE of .27, and a Relative RMSE of .41.
- The Random Forest regressor model performed quite well with an EV of .59, MAE of 30, RMSE of 49, RMAE of .19, and a Relative RMSE of .32.
- The Deep Learning model moderately well, however, did not yield improvement over the random forest regressor. The model using early stopping had an EV of .41, MAE of 39, RMSE of 60, RMAE of .25, and a Relative RMSE of .39.

Without Reviews - Availability

- The simple linear regression model performed moderately well, however relative RMSE and RMAE metrics were very high. EV of .32, MAE of 8, RMSE of 10, RMAE of .70, and a Relative RMSE of .84.
- The Random Forest regressor model performed better with an EV of .54, MAE of 6, RMSE of 8, RMAE of .5, and a Relative RMSE of .7.
- The Deep Learning model performed well, however, did not yield improvement over the random forest regressor. The model using early stopping had an EV of .44, MAE of 7, RMSE of 9, RMAE of .62, and a Relative RMSE of .77.
