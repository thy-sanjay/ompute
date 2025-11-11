# Ompute

**Ompute** is a Python package for **omics data missing value imputation**, providing a unified interface to 22 individual and 10 Tribrid imputation models.
Each model implements a reproducible classical, machine-learning, bayesian, or hybrid strategy to handle MCAR, MAR, and MNAR missing values in omics datasets.

Python Package Link: https://pypi.org/project/ompute/

---

## Imputation Model Details

### Individual Imputation Models

| Category | Model Name |
|-----------|-------------|
| **MCAR** | Mean Imputation |
| **MCAR** | Median Imputation |
| **MCAR** | Mode Imputation |
| **MCAR** | Hot-Deck Imputation |
| **MCAR** | KNN Imputation |
| **MCAR** | MissForest Imputation |
| **MCAR** | PPCA / BPCA |
| **MCAR** | SVD / SoftImpute |
| **MCAR** | Expectation-Maximization (EM) |
| **MAR** | MICE / Iterative Imputer |
| **MAR** | Linear / ElasticNet Regression Imputation |
| **MAR** | Random Forest Regression Imputation |
| **MAR** | Local Least Squares (LLS / LSA) |
| **MAR** | SoftImpute (Matrix Completion) |
| **MAR** | MissMDA (PCA Iterative) |
| **MAR** | Bayesian Regression (DPR) |
| **MAR** | Autoencoder Imputation |
| **MNAR** | MinDet (Minimum Detection Limit) |
| **MNAR** | MinProb (Minimum Probability) |
| **MNAR** | Perseus Downshifted Normal |
| **MNAR** | Truncated Normal Imputation |
| **MNAR** | QRILC (Quantile Regression Imputation of Left-Censored) |

---

### Tribrid (Hybrid) Models

| Model | MCAR Component | MAR Component | MNAR Component |
|:------|:---------------|:---------------|:----------------|
| **trb1** | KNN Imputation | MissForest Imputation | QRILC |
| **trb2** | KNN Imputation | Random Forest Regression | QRILC |
| **trb3** | Mean Imputation | MICE / Iterative Imputer | MinProb |
| **trb4** | Median Imputation | Linear / ElasticNet Regression | Perseus Downshifted Normal |
| **trb5** | Mode Imputation | MissForest Imputation | MinDet |
| **trb6** | Hot-Deck Imputation | Local Least Squares (LLS / LSA) | Truncated Normal Imputation |
| **trb7** | KNN Imputation | MissForest Imputation | Perseus Downshifted Normal |
| **trb8** | SVD / SoftImpute | MissMDA (PCA Iterative) | QRILC |
| **trb9** | PPCA / BPCA | MICE / Iterative Imputer | MinProb |
| **trb10** | KNN Imputation | Random Forest Regression | MinDet |

---

## Usage

Each model can be executed directly as a function once the package is installed.

```python
pip install ompute
import ompute

# Example 1: Run an individual model
ompute.knn(i="data/input.csv", d="data/expdes.csv", o="/results")

# Example 2: Run a Tribrid model
ompute.trb1(i="data/input.csv", d="data/expdes.csv", o="/results")

# Example 3: Get imputed data as a pandas DataFrame
df = ompute.mean(i="data/input.csv", d="data/expdes.csv", o="/results", return_df=True)

