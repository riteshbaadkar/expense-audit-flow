# Expense Audit Flow

A machine learning classifier that audits financial transactions and 
automatically flags suspicious entries for human review.

Built on a real-world dataset of 1.2 million transactions.

---

## Problem Statement

Financial fraud costs businesses billions annually. Manual auditing of 
every transaction is impossible at scale. This project builds an 
automated classifier that identifies high-risk transactions, allowing 
audit teams to focus their attention where it matters most.

---

## Dataset

Source: [Synthetic Financial Fraud Dataset](https://www.kaggle.com/datasets/kartik2112/fraud-detection)  
Rows: 1,296,675 transactions  
Fraud rate: 0.58% (highly imbalanced)

---

## Project Structure

expense-audit-flow/
├── data/               ← Dataset (not tracked in Git — download from Kaggle)
├── notebooks/          ← Jupyter notebooks with analysis and charts
├── scripts/            ← Standalone Python scripts
├── requirements.txt    ← Required libraries
└── README.md

---

## Key Findings

1. **Class imbalance:** Only 0.58% of transactions are fraudulent.
   Accuracy is a misleading metric — F1 score was used instead.

2. **High-risk category:** Grocery (in-store) and online shopping were the two highest risk categories, with approximately 1,750 flagged transactions each — nearly double every other category.

3. **Time pattern:** Fraud rate peaks at late night hours — peaking at 2.85% between 10pm and midnight, and a secondary peak of 1.5% between midnight and 3am. During regular daytime hours (4am–9pm) the fraud rate drops to nearly zero — suggesting fraudulent activity is heavily concentrated in low-monitoring overnight hours.

4. **Distance signal:** Transactions occurring far from the 
   cardholder's home location showed higher fraud rates.

---

## Models

| Model | F1 Score |
|---|---|
| Logistic Regression | 0.14 |
| Decision Tree (depth=10) | 0.43 |

The Decision Tree performed better, with 96% 
recall on fraudulent transactions.

---

## How to Run

1. Clone this repository
2. Download the dataset from Kaggle and place `fraudTrain.csv` in the `data/` folder
3. Install requirements: `pip install -r requirements.txt`
4. Open Jupyter: `jupyter notebook`
5. Run `notebooks/01_data_exploration.ipynb` from top to bottom

---

## Tech Stack

- Python 3
- Pandas — data manipulation
- SQLite — database storage and SQL queries
- Matplotlib & Seaborn — visualisation
- Scikit-learn — machine learning models
