# Time Series Forecasting: AirPassengers Dataset

## Overview

This project demonstrates time series forecasting using the classic AirPassengers dataset. The workflow includes:
- Data preprocessing and stationarity transformation
- ARIMA model training and evaluation
- Expanding window cross-validation for one-step and multi-step forecasting
- Visualization and error analysis

## Dataset

- **Source:** `https://www.kaggle.com/datasets/rakannimer/air-passengers`
- **Description:** Monthly totals of international airline passengers, 1949–1960.

## Workflow

### 1. Data Preparation
- Load the dataset and parse dates.
- Visualize the raw time series.
- Test for stationarity using the Augmented Dickey-Fuller (ADF) test.

### 2. Stationarity Transformation
- Apply log transformation to stabilize variance.
- Apply seasonal differencing (lag 12) and first-order differencing to remove trend and seasonality.
- Confirm stationarity with ADF test and ACF/PACF plots.

### 3. Model Training
- Split data into training and test sets (`test period = 1958-01-01 to 1960-12-01`).
- Fit an ARIMA model on the stationary series.
- Print and interpret the model summary.
- Plot fitted values vs. actuals for the training set.
- Compute and plot residuals.

### 4. Model Evaluation
- Forecast the test set using the trained model.
- Inverse-transform predictions to the original scale.
- Compute Mean Absolute Percentage Error (MAPE).
- Plot actual vs. forecasted values.

### 5. Expanding Window Cross-Validation
- Implement expanding window CV for:
  - **One-step forecasting** (window=1, start date: 1957-12-01)
  - **Multi-step forecasting** (window=3)
- For each, plot predictions vs. actuals and compute MAPE.

## How to Run

1. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Run the notebook or script:**
   - Open the `TSA_air_passenger.ipynb` notebook and run all cells **OR**
   - Run the Python script if provided.

3. **Suppress warnings (optional):**
   Add these lines after your imports:
   ```python
   import warnings
   warnings.filterwarnings('ignore')
   ```

## Key Files

- `data/AirPassengers.csv` — The dataset
- `TSA_air_passenger.ipynb`  — Main analysis and modeling code

## Results

- **One-step Expanding Window MAPE:** ~12%
- **Multi-step Expanding Window MAPE:** ~21%
- The ARIMA model captures the trend and seasonality, with reasonable forecast accuracy.

## Notes

- For improved seasonal modeling, consider using SARIMA.
- You can further tune ARIMA orders based on ACF/PACF plots.
- The code includes all necessary inverse transformations for accurate evaluation.

## License

This project is for educational purposes. 