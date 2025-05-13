# 📊 Machine Learning-Driven Portfolio Optimization using Clustering and Ensemble Learning

This project presents a robust framework for **portfolio optimization** using **machine learning models** enhanced with **clustering techniques** and **Markowitz-based risk weighting**. The work focuses on stock selection within the **S&P 500 index**, applying various financial indicators and historical patterns to predict returns and build optimized, dynamically rebalanced portfolios.

---

## 📌 Overview

### Objectives:
- Predict future stock returns using ensemble machine learning models.
- Improve asset selection and diversification using clustering (KMeans, Birch).
- Integrate Markowitz risk-aware weighting for robust portfolio construction.
- Evaluate risk-adjusted metrics like Sharpe, Sortino, Max Drawdown, VaR/CVaR.

---

## 🧠 Methodology

### 📥 Data Collection & Preprocessing
- Historical OHLCV data and technical indicators (RSI, MACD, SMA, EMA, etc.)
- Integrated fundamental features: P/E Ratio, ROE, Market Cap
- Feature scaling via `StandardScaler`
- Missing values filled using median (excluding key financials)

### 🧩 Clustering
- **KMeans & Birch Clustering** to group stocks by behavior
- Cluster ratings assigned based on average **Sharpe Ratio** and **Drawdown**
- Added as categorical features to ML models

### 🧮 Markowitz Weighting
- Monthly inverse-variance weighting to signal low-risk, high-return assets
- Weights merged as features

### 🤖 Machine Learning Models
- **Neural Network (Keras)**: Deep MLP with dropout & batch normalization
- **XGBoost Regressor**
- **LightGBM Regressor**
- Target variable: M-day Future Return

### 🧪 Ensemble Modeling
- Simple average ensemble of 3 models
- Prevents overfitting and improves generalization

### 📈 Portfolio Simulation
- Top N predicted return stocks selected at each rebalance (M-day interval)
- Weighted using softmax of predicted return
- Performance tracked daily with risk metrics

---

## 📊 Results

| Configuration         | Sharpe | Max Drawdown | Annual Return | Sortino | Calmar |
|-----------------------|--------|---------------|----------------|---------|--------|
| Markowitz + Clustering| 4.29   | -4.4%         | 123.3%         | 6.98    | 27.94  |
| Clustering Only       | 1.28   | -8.0%         | 30.4%          | 1.79    | 3.77   |

📌 ML Model MAEs:  
- Neural Net: 0.01318  
- XGBoost: 0.01318  
- LightGBM: 0.01390  



