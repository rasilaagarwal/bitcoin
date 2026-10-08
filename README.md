# Bitcoin Next-Day Direction Prediction (Task A)

Big Data Analytics (BDA) assignment. The project predicts whether Bitcoin's closing price will be **higher (UP) or lower (DOWN) tomorrow** than today, following the KDD process (Selection, Pre-processing, Transformation, Data Mining, Evaluation).

**Author:** Rasila Agarwal

## Files

| File | Description |
|---|---|
| `assignment.py` | Python code: data preparation, features, and the four models |
| `bitcoindata.csv` | Daily Bitcoin data (Date, High, Low, Close, Volume) aggregated from 1-minute data |
| `index.html` | Interactive dashboard comparing the algorithms (published with GitHub Pages) |

## Data

The original dataset has about 7.76 million one-minute BTC/USD rows (393 MB), which is too large for GitHub.
`bitcoindata.csv` contains the same data aggregated to daily candles (High = max, Low = min, Close = last, Volume = sum).
Original data source: [add the link where you downloaded the dataset].

## Method

- **Features (8):** 1/5/10-day returns, 10-day volatility, price vs 10/50-day moving average, daily range, volume change.
- **Target:** 1 if tomorrow's close is higher than today's close, otherwise 0.
- **Split:** older half of the days for training, newer half for testing (no shuffling).
- **Algorithms:** Logistic Regression, SVM (RBF), Random Forest, K-Nearest Neighbours.
- **Baseline:** always predicting UP.

## Results (2012-2013 window, 341 test days)

| Algorithm | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| Logistic Regression | 0.610 | 0.617 | 0.972 | 0.755 |
| SVM (RBF) | 0.619 | 0.619 | 1.000 | 0.764 |
| Random Forest | 0.531 | 0.595 | 0.758 | 0.667 |
| KNN (k=31) | 0.566 | 0.625 | 0.749 | 0.681 |
| *Baseline: always UP* | *0.619* | *0.619* | *1.000* | *0.764* |

**Conclusion:** no algorithm beat the always-UP baseline. In 2013 most days were UP days (Bitcoin rose sharply), so an accuracy of about 0.62 reflects the market, not model skill.

## How to run

```bash
pip install pandas numpy scikit-learn
python assignment.py
```

Make sure `bitcoindata.csv` is in the same folder as `assignment.py`.

## Dashboard

Open `index.html` locally, or use the GitHub Pages link: `https://rasilaagarwal.github.io/bitcoin/`
