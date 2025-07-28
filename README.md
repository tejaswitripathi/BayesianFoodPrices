# Bayesian Modeling of Retail Price Spreads 🧠📈  
*Analyzing the relationship between farm prices and retail price markups using Bayesian inference techniques.*

## 🧠 Project Overview  
This project uses Bayesian regression to understand how **"averagespread"** (i.e., the markup from **farm price** to **retail price**) varies by **product type**. We compare linear and interaction models to identify which best captures product-specific effects in pricing trends.

## 📊 Dataset Description  
The dataset includes **8 features**, with two key ones:
- `farmprice`: price of a product at the farm level  
- `averagespread`: markup amount between farm and retail prices

Each entry is also associated with a **product name**, which is hypothesized to affect the relationship.

## 🔍 Exploratory Analysis  
- Initial cleanup and plotting of `farmprice` vs `averagespread` revealed a **nonlinear inverse trend**, roughly resembling `y = 1/x`.
- Visual inspection suggested that **different products exhibit distinct pricing behaviors**.

## 🧪 Bayesian Models Tested

### 📌 Model 1: Linear Regression  
- Fit using standard Bayesian inference (likely via MCMC)  
- All **neff_ratios** and **R-hats** were within acceptable convergence ranges  
- However, **posterior predictive checks** revealed limited predictive accuracy

### 📌 Model 2: Interaction Model  
- Added **interaction between product name and farmprice**  
- R-hats were solid, but **neff_ratios** were less stable, possibly due to model complexity  
- Despite convergence concerns, this model **performed significantly better** on predictive tasks

## ✅ Model Evaluation  
- Used **LOO (Leave-One-Out) cross-validation** with `loo_compare()`  
- **Interaction model outperformed the linear model** by a large margin  
- This confirms the hypothesis: each product has a **unique relationship** between farmprice and averagespread

## 🔧 Suggested Improvements  
- Use a **hierarchical model** to fit a sub-model per product — this would allow for both group-level trends and product-level nuance  
- Apply **random forest regression** or **PCA** to assess which products contribute most to variance in `averagespread`  
- Could improve **sampling efficiency** with better priors or reparameterization

## 💻 Tools & Techniques  
- Bayesian modeling libraries (e.g., `PyMC`, `Stan`, `Bambi`)  
- LOO validation for model comparison  
- Posterior predictive checks  
- Exploratory visualization

## 📁 Suggested Directory Structure  
```
bayesian-retail-pricing/
│
├── data/                   # Raw and cleaned datasets
├── notebooks/              # Jupyter notebooks with modeling code
├── models/                 # Saved posterior traces or compiled models
├── src/                    # Scripts for preprocessing, inference, plotting
├── results/                # LOO results, PPCs, summary tables
├── README.md
└── requirements.txt        # Python dependencies
```

## ✍️ Author  
Tejaswi Tripathi
