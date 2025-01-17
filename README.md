# Wind energy prediction demo

## Summary

The project studies data-driving methods of wind power analysis and prediction. Due to a sequential nature of wind power, LSTM models were chosen to build short-term forecasts. It was shown that a CNN-LSTM approach allows to reach a better fit compared to a base LSTM model.

## Background

The currect project aims to solve the following issues:
* Prove that adding more meteorological data might help to improve the quality of forecasts. It was demonstrated by applying multivariate, one-step long short-term memory (LSTM) networks. 
* Multivariate, multi-step deep learning networks were built for predicting wind power within 12h and 24h ahead. Here, CNN-LSTM network showed a higher accuracy compared with a case of applying LSTM network. 

## How is it used?

The project was implemented using [Python](https://www.python.org/) as the main source for writing codes. First it was required to read .csv files from ENGIE, merge them, preprocess data and then complete this dataset with data available from MERRA-2 project. This enriched dataset was then used for all wind forecasts (70% of data is a training set, 10% - a validation set, and remaining 20% - a test set).

## Data sources

Historical in situ measurements for the La-Haute-Borne wind park were available from [ENGIE](https://opendata-renewables.engie.com/) and global reanalysis data were taken as a part of MERRA-2 project from [NASA](https://gmao.gsfc.nasa.gov/reanalysis/MERRA-2/).

## Results

The main drawback of applying multivariate, one-step LSTM method is that in this case the whole test dataset is forecasted at once, which is not how it really happens. Thus, to improve the quality of the forecasts we need to apply multivariate, multi-step LSTM and CNN-LSTM scheme. 

Figure below shows comparison between three cases - when additional weather parameters from MERRA-2 project were ignored within the forecast (Case 1 with pink markers), used partially (only outdoor temperature, Case 2 with green markers) or fully (temperature, pressure, humidity - Case 3 with blue markers). The RMSE values were 0.236 for Case 3, 0.241 for Case 2, and 0.256 for Case 1.

![weather](https://github.com/Mandzhi/Open_wind_La-Haute-Borne/blob/main/LSTM-one-step.jpg)

Another figure demonstrates comparison between multi-variate CNN-LSTM and LSTM models for 24 hours. Here it can be seen that CNN-LSTM model was able to capture almost all fluctuations in a proper manner, while a base LSTM network could only to follow the averaged trend. 

![cnn-lstm_vs_lstm](https://github.com/Mandzhi/Open_wind_La-Haute-Borne/blob/main/LSTM_multi_24h.jpg)

## Challenges

The current project was only focused on the short-term forecasts, therefore, it did _not_ consider applications of data-driven methods for the long-term wind predictions. This could be the next step of the project.

## What next?

In addition to application of data-driven methods for long-term forecasts, it can be interesting to investigate some other available deep learning techniques that also might be good at predicting sequential data.

## Licence

If you are going to use [ENGIE](https://opendata-renewables.engie.com/) dataset to practise, please notice that it has its own [LICENCE](https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf).

## Acknowledgments

ENGIE Renewables is acknowledged for sharing their "La Haute Borne" dataset with researchers. It indeed helps to feel how difficult is to work with raw data. Gratitudes should also be sent to the Global Modeling and Assimilation Office (GMAO) at NASA Goddard Space Flight Center for the MERRA-2 reanalysis data which was provided through the NASA GES DISC online archive. And I would like to thank BuildingAI course for encouraging me to make this project available via GitHub :)
