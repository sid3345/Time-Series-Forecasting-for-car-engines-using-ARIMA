# Time-Series-Forecasting-for-car-engines-using-ARIMA
### ARIMA (Auto-Regressive Integrated Moving Averages) is a very popular statistical method for time series forecasting. 

ARIMA models works on following assumptions –

The data series is stationary, i.e mean and variance should not vary with time. A series can be made stationary by using log transformation or differencing the series.

The data provided as input must be a univariate series, since ARIMA uses the past values to predict the future values.

### ARIMA has three components – AR (autoregressive term), I (differencing term) and MA (moving average term). 

Steps for ARIMA implementation:
1.	Load the data 
2.	 Preprocessing
3.	Make series stationary: In order to satisfy the assumption, it is necessary to make the series stationary. This includes checking the stationarity of the series and performing required transformations
4.	Determine d value: For making the series stationary, the number of times the difference operation was performed will be taken as the d value
5.	Create ACF and PACF plots:  ACF PACF plots are used to determine the input parameters for our ARIMA model
6.	Determine the p and q values
7.	Fit ARIMA model
8.	Predict values on validation set 
9.	Calculate MSE 

### Why Auto ARIMA?  (Documentation: http://alkaline-ml.com/pmdarima/0.9.0/modules/generated/pyramid.arima.auto_arima.html)

Although ARIMA is a very powerful model for forecasting time series data, the data preparation and parameter tuning processes are very time consuming and complex. 

Before implementing ARIMA, we need to make the series stationary, and determine the values of p and q using the plots. Auto ARIMA simplifies this task, as it eliminates steps 3 to 6. 

Below are my steps for implementing auto ARIMA:
1.	Load the data: CSV file

2.	Preprocessing data: The input should be univariate, hence dropped other columns. Separating engines by engine ID. Engine 2 (both operating hours & fuel consumption), 17 (both operating hours & fuel consumption) and 19 (fuel consumption) are constant rates. May be they are ambiguous, thus model cannot be applied and forecast is the same constant.

3.	Fit Auto ARIMA: Fit the model on the univariate series

4.	Predict values on validation set: Make predictions on the validation set. Training set: 80 days. Testing (Validation) set: 20 days.

5.	Calculate MSE: Check the performance of the model using the predicted values against the actual values. MSE (Mean squared error) used.

Using AutoARIMA selection of p and q features are bypassed as it automatically discovers the optimal order for an ARIMA model.

Accuracy may be less as dataset is very small (100 days), for ARIMA to work perfectly, as it uses moving averages.
