# Overview

## Project on developing predictive model in detecting and preventing forest fires in Algerian regions.

### Introduction
In the Algerian regions (Northern Africa) of Bejaia and Sidi Bel-abbes during the period, between June 2012 and September 2012, forest fires ravaged an estimated 20,000 hectares of land. This project aims to construct a prediction model for forest fires and we will use the Algerian Forest Fires Dataset [Faroudja,2019], which contains data from two sub-regions.

The target variable for this project will be the Classes label from the dataset [Faroudja,2019], and we will perform K-nearest neighbours classification algorithm to answer the predictive question.

### Brief data explanation
* Temperature: Degree Celsius
* RH: Relative Humidity (%)
* Ws: Wind speed (km/h)
* ISI (Initial Spread Index): estimation of the anticipated spread of a fire that is based on FFMC.
* FFMC (fine fuel moisture code): the moisture content based on litter or other fine fuels.
* DMC (Duff Moisture Code) and DC (Drought Code): is the average rating of moisture in the organic layers of the forest.
* BUI (Buildup Index): the total amount of fuel that can be used for a combustion reaction, this number is based on the DMC and the DC.
* FWI (Fire Weather Index): the rating of the strength of the fire.

### Exploratory Steps¶
- Splitting the dataset into training and testing sets.
- Creating visualization by ggpairs() function to check whether the data is imbalanced as well as to determine the predictors for the model specification.
- Adding plots of predictors respectively for the better understanding and demonstration on the data distribution.

## Model Training and Tuning
* Creating model specification with tune() (in order to select the best K from following analysis steps).
* Including the selected predictors from the exploratory steps which are FWI, FFMC, BUI, ISI respectively in recipe.
* Performing 5-fold cross-validation on the training dataset and chaining together data analysis steps by workflow().
* Picking a K value that yields the highest accuracy and doesn't decrease accuracy too much when changing it to the nearby ones.

## Evaluating Accuracy
* Retraining the model specification with K = 7
* Predicting the labels on testing set to evaluate classifier's accuracy.

## Visualization of the Analysis
* Outputing the accuracy statistics in a matrix. 
* Plotting the decision boundaries for the classification result. (Since there are more than two predictors, two decision boundaries plots are created).

### Results and Discussion
We found that this model will have the ability to predict the existence of future forest fires with an accuracy above 96%, based on the FWI, FFMC, BUI, and ISI of the region. This accuracy is 11% higher than we initially expected from the proposal.

This prediction model can be applied proactively as a means to prevent future forest fires in vulnerable regions by performing controlled burns in areas where forest fires are expected, thus making it a valuable environmental tool. Scaffolding from this model could possibly be extrapolated to fit the model for regions other than Bejaia and Sidi Bel-abbes, as well as countries other than Algeria.


### References
Faroudja ABID et al., Predicting Forest Fire in Algeria using Data Mining Techniques: Case Study 
    of the Decision Tree Algorithm, International Conference on Advanced Intelligent 
    Systems for Sustainable Development (AI2SD 2019) , 08 - 11 July , 2019, Marrakech, 
    Morocco.

Alonso-Betanzos, A., et al. (2003). An intelligent system for forest fire risk prediction and fire 
    fighting management in Galicia. Expert Systems with Applications, 25(4), 545-554. 
    https://doi.org/10.1016/S0957-4174(03)00095-2

Cheng, T., & Wang, J. (30 September 2008). Integrated Spatio‐temporal Data Mining for Forest 
    Fire Prediction. Transactions In GIS, 12(5), 591-611.  
    https://doi.org/10.1111/j.1467-9671.2008.01117.x
