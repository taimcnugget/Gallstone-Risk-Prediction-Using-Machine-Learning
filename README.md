# Gallstone-Risk-Prediction-Using-Machine-Learning

## 🌟Highlights
Two supervised learning models were evaluated using identical train–test splits and a fixed classification threshold to enable direct comparison.

- **Random Forest achieved substantially higher precision**, indicating fewer false-positive gallstone predictions.
- **Logistic Regression demonstrated higher recall**, identifying a greater proportion of true gallstone cases.
- **Overall F1 scores were comparable**, suggesting a tradeoff between sensitivity and specificity rather than a clear dominance of one model.
- **ROC-AUC was higher for the Random Forest**, reflecting improved ranking performance across probability thresholds.

These results highlight a meaningful precision–recall tradeoff between linear and non-linear modeling approaches. Model selection may therefore depend on the downstream application and the relative cost of false positives versus false negatives.

Notably, the two highest-ranked features identified across statistical and model-based importance measures, Vitamin D[1] and C Reactive Protein (CRP)[2], have been previously reported in the clinical literature as risk factors associated with gallstone formation. This concordance provides external validation that the models captured clinically meaningful relationships rather than spurious correlations.

## Project Overview
Gallstones are a common gastrointestinal condition influenced by demographic and physiological risk factors. The goal of this project was to build and evaluate machine learning models that predict gallstone presence using patient-level clinical and demographic data, while emphasizing **model interpretability, evaluation rigor, and decision-making tradeoffs** rather than model complexity.

This project compares a traditional linear classifier with a non-linear ensemble model and examines feature importance using both **statistical** and **model-based** approaches.

## Objectives
- Develop a supervised learning pipeline to predict binary gallstone status
- Compare model performance between:
    - Logistic Regression (interpretable baseline)
    - Random Forest (non-linear ensemble)
- Evaluate classification performance using clinically relevant metrics
- Analyze feature importance using multiple methodologies
- Avoid overfitting and unnecessary model complexity

## Dataset
The original data was collected by Esen, I., Arslan, H., Aktürk, S., Gülşen, M., Kültekin, N., & Özdemir, O. (2024). Gallstone [Dataset]. UCI Machine Learning Repository.[3](https://doi.org/10.1097/md.0000000000037258).

The dataset consists of patient-level features including:

- Demographic variables
- Binary clinical indicators
- Continuous physiological measurements

Target variable:
- **Gallstone Status** (binary classification)

Key preprocessing notes:
- No missing values were present in the dataset
- Continuous features were standardized where required (logistic regression)
- Class balance was evaluated prior to model training

## Tools & Libraries
- Python
- pandas, NumPy
- scipy stats
- scikit-learn
- matplotlib / seaborn

## Modeling Approach
### 1. Logistic Regression
Logistic regression was used as a baseline model due to:
- Interpretability of coefficients
- Suitability for binary outcomes
- Ability to estimate calibrated probabilities

Feature scaling was applied prior to model fitting to ensure numerical stability and convergence.

### 2. Random Forest Classifier

A random forest model was implemented to:

- Capture non-linear relationships
- Model feature interactions
- Compare performance against a linear baseline

The same train–test split and classification threshold were used across models to enable fair comparison.

## Model Evaluation
Models were evaluated using:

- **Precision**
- **Recall**
- **F1 Score**
- **ROC-AUC**

A fixed probability threshold was used across models to isolate differences in learning behavior rather than decision policy.


## Feature Importance Analysis
Feature relevance was assessed using three complementary approaches:

1. **ANOVA F-scores**
    - Measures univariate statistical association with the target
2. **Logistic regression coefficients**
    - Direction and magnitude of linear relationships
3. **Random forest feature importance**
    - Model-based, non-linear importance

To enable comparison across methods, importance scores were normalized using min–max scaling.

This multi-perspective approach provides robustness when interpreting feature contributions.

## Key Findings
- Logistic regression and random forest models demonstrated comparable predictive performance
- Certain features consistently ranked highly across statistical and model-based importance measures
- Random forest captured non-linear effects but did not dramatically outperform the linear baseline, suggesting a relatively structured feature–outcome relationship


## Limitations
- The dataset is static and does not include longitudinal measurements
- No external validation cohort was available
- Threshold optimization was explored but not tuned for deployment-specific cost functions


## Future Work
- Incorporate cost-sensitive threshold optimization
- Validate model performance on an independent dataset
- Extend analysis to temporal or longitudinal data if available

## Literature
[[1]](https://pubmed.ncbi.nlm.nih.gov/39261120/) Bin C, Zhang C. The association between vitamin D consumption and gallstones in US adults: A cross-sectional study from the national health and nutrition examination survey. J Formos Med Assoc. 2025 Mar;124(3):212-217. doi: 10.1016/j.jfma.2024.09.010. Epub 2024 Sep 11. PMID: 39261120.

[[2]](https://pmc.ncbi.nlm.nih.gov/articles/PMC11588438/) Jiang Z, Jiang H, Zhu X, Zhao D, Su F. The relationship between high-sensitivity C-reactive protein and gallstones: a cross-sectional analysis. Front Med (Lausanne). 2024 Nov 12;11:1453129. doi: 10.3389/fmed.2024.1453129. PMID: 39600934; PMCID: PMC11588438.
