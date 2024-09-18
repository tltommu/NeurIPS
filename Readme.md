# Ariel Data Challenge 2024 - Optimized Solution

This repository contains an optimized approach for the **Ariel Data Challenge 2024**. The core implementation is derived from several expert kernels, including the works of yukiZ, qianc, and Sergei Fironov, with significant optimizations and updates to the solution pipeline.

## Overview

This solution is based on an ensemble of multiple techniques and kernels that have proven effective in improving model accuracy. Specifically, this solution filters and enhances the best-performing options from the Ariel | Ensemble of Solutions notebook.

### Key Notebooks Referenced:
- **ariel_only_correlation | param upd[LB.517] by yukiZ**: A correlation-based parameter update achieving a leaderboard score of 0.517.
- **qianc's Notebook (LB = 0.545)**: Advanced model featuring derivative-based signal start and end detection during eclipses, with further optimizations to polynomial fitting and signal correction.

## Approach and Implementation

### Main Techniques:
1. **Linear Correction Application**: We apply a linear correction to the signal data using polynomial fitting techniques to remove systematic noise.
2. **Dark Frame and Dead Pixel Correction**: The signal data is cleaned by removing dark frames and compensating for dead or hot pixels.
3. **Signal Binning**: We reduce the signal's dimensionality by binning, which aggregates and averages the data, allowing for more efficient processing without losing significant information.
4. **Signal Calibration**: Polynomial fitting is used to calibrate the signal. The polynomial degree is determined dynamically by minimizing the error between the predicted and actual signal.
5. **Ridge Regression Model**: After feature engineering, we train a Ridge regression model on the processed signals to predict the test results. This model is combined with other ensembled solutions.

### Signal Processing Functions:
- **apply_linear_corr**: Applies linear correction to the input signal based on calibration data.
- **clean_dark**: Cleans the signal by subtracting the dark frame and compensating for exposure time.
- **preproc**: Main preprocessing function that handles loading, cleaning, and feature extraction for each sensor (AIRS-CH0 and FGS1).
- **phase_detector**: Identifies key phases in the signal during the planetary eclipse.
- **calibrate_signal & calibrate_train**: Functions for calibrating the signal using polynomial fitting techniques.

## Dependencies

This project uses the following Python libraries:
- `pandas`
- `numpy`
- `scipy`
- `matplotlib`
- `seaborn`
- `astropy.stats`
- `scikit-learn`

## File Descriptions

- **notebook.ipynb**: Contains the entire processing and model pipeline, including feature engineering, signal correction, and Ridge regression training.
- **pre_train**: Pre-processed training data used for model training.
- **submission_7.csv**: Submission file for the challenge containing predictions for the test set.

## How to Run the Code

1. Clone the repository.
2. Ensure that all the required dependencies are installed. You can install them by running:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Jupyter Notebook `notebook.ipynb` to process the data and generate predictions.
4. Submit the generated `submission.csv` to the Ariel Data Challenge 2024.

## Updates

- **2024/09/08**: Updated `scipy.minimize()` parameters and optimized other hyperparameters based on performance testing.

## Acknowledgements

- **yukiZ**: For the foundational work on correlation-based parameter updates.
- **qianc**: For the optimized signal processing and derivative-based eclipse detection.
- **Sergei Fironov**: For the original work on the Ariel correlation model.

This project is an ensemble of solutions from several expert participants, refined for better performance in the Ariel Data Challenge 2024.

