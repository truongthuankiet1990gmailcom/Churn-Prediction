# Customer Churn Analysis and Prediction
<img src = "Images/dataset_cover.png">

This project analyzes customer churn for a telecommunications company (MCI) using machine learning models. The goal is to identify key drivers of churn, build predictive models, and provide actionable insights to improve customer retention.

---
# Dataset

- **Training set:** `Copy of churn-bigml-80.csv`
- **Test set:** `Copy of churn-bigml-20.csv`
- Each row represents a customer with features such as usage statistics, service plans, and churn status.

---
# What is the significance of Churn Rate for stakeholders (Customers, MCI, etc.)?
The Churn Rate is a critical business metric that measures the percentage of customers who stop using a company’s services over a specific period. Its significance for stakeholders, such as customers and MCI (a telecommunications company), includes:

- **For Customers:**
    - Churn rate reflects customer satisfaction and service quality. A high churn rate may indicate dissatisfaction due to poor service, high costs, or better alternatives elsewhere, prompting customers to switch providers.
    - Understanding churn helps customers indirectly, as companies like MCI may improve services, offer better pricing, or enhance customer support to retain them.
- **For MCI (the Company):**
    - Financial Impact: Retaining existing customers is 5–25 times less expensive than acquiring new ones. High churn rates lead to revenue loss and increased marketing costs to replace lost customers.
    - Customer Lifetime Value (CLV): Churn reduces CLV, as long-term customers generate more revenue through subscriptions and upsell opportunities. Reducing churn maximizes CLV.
    - Operational Efficiency: By identifying at-risk customers, MCI can focus retention efforts (e.g., targeted promotions, improved support) on high-value customers, optimizing resource allocation.
    - Competitive Positioning: A low churn rate signals strong customer loyalty and service quality, giving MCI a competitive edge in the telecommunications market.
- **For Other Stakeholders (e.g., Investors, Employees):**
    - Investors view low churn as a sign of business stability and growth potential, impacting stock value and investment decisions.
    - Employees benefit from a stable customer base, as it supports job security and opportunities for performance-based incentives.
    - By monitoring and reducing churn, MCI can enhance customer satisfaction, improve profitability, and strengthen its market position.

# What are the characteristics of each type of customer (Churn or Not Churn)?
## Numerical Features
<img src = "Images/numerical_features.png">

**Summary of Characteristics**

- **Churned Customers:**
    - Higher usage and charges: More Total Day Minutes (~ 210 vs. 180), Total Day Charge (~ $35 vs. $30), Total Intl Minutes (~ 12 vs. 10), and Total Intl Charge (~$3.2 vs. $2.7).
    - More Customer Service Calls (~ 2–2.5 vs. 1.5), with a notable tail at 4+ calls.
    - Slightly higher evening usage (Total Eve Minutes ~ 210 vs. 200, Total Eve Charge ~$18 vs. $17).
    - Less likely to use voicemail (lower Number vmail messages, mean ~ 5 vs. 8–10).
    - Similar account length, call frequencies (day, evening, night), and night usage/charges.
- **Non-Churned Customers:**
    - Lower usage and charges: Total Day Minutes (~ 180), Total Day Charge (~ $30), Total Intl Minutes (~ 10), Total Intl Charge (~ $2.7).
    - Fewer Customer Service Calls (mean ~ 1.5, mostly 0–2 calls).
    - More likely to use voicemail (higher Number vmail messages, mean ~ 8–10).
    - Similar account length, call frequencies, and night usage/charges.

**Key Insights**
- **Cost Sensitivity:** Churned customers have higher daytime and international charges, suggesting cost is a major churn driver.
- **Service Issues:** More customer service calls among churned customers indicate dissatisfaction or unresolved complaints.
- **Engagement:** Lower voicemail usage among churned customers suggests they are less engaged with value-added services.
- **Usage Patterns:** Higher daytime and international usage among churned customers may lead to bill shock, prompting them to switch providers.

## Categorical Features
<img src = "Images/state.png">
<img src = "Images/categorical_features.png">

**Summary of Characteristics**
- **Churned Customers:**
    - **Area Code:** Similar distribution to non-churned (415: 50.3%, 408: 24.2%, 510: 25.5%), with churn rates of 14.5%–15.2%. Area code is not a strong predictor of churn.
    - **International Plan:** Much more likely to have an international plan (30.4% vs. 6.7% for non-churned). Churn rate for those with an international plan is very high (44.5%).
    - **Voice Mail Plan:** Less likely to have a voice mail plan (16.8% vs. 29.3% for non-churned). Churn rate is higher without a voice mail plan (17.2% vs. 9.2%).
    - **State (from previous analysis):** More likely to be from high-churn states like NJ (~50%), TX (~25%), MD (~25%), WA (~25%), and CA (~25%).
- **Non-Churned Customers:**
    - **Area Code:** Evenly distributed (415: 49.3%, 408: 25.2%, 510: 25.5%), with churn rates close to the overall average.
    International Plan: Rarely have an international plan (6.7%), with a lower churn rate (11.6%) for those without.
    - **Voice Mail Plan:** More likely to have a voice mail plan (29.3%), which correlates with a lower churn rate (9.2%).
    - **State (from previous analysis):** More likely to be from low-churn states like HI (~5%), AK (~5%), VA (~8%), IA (~5%), and RI (~6%).

**Key Insights**
- **International Plan as a Churn Driver:**
    - Customers with an international plan have a 44.5% churn rate, compared to 11.6% for those without. This is a major differentiator, suggesting issues like high costs or poor service quality for international plans.
- **Voice Mail Plan as a Retention Tool:**
    - Customers with a voice mail plan have a lower churn rate (9.2% vs. 17.2%). Offering or promoting voice mail plans could enhance engagement and reduce churn.
- **Area Code Not a Factor:**
    - Churn rates across area codes are nearly identical (14.5%–15.2%), indicating that geographic area codes don’t significantly influence churn behavior.
- **State-Level Variations:**
    - High churn in states like NJ, TX, and CA may reflect regional competition or service issues, while low churn in HI, AK, and VA suggests stronger customer loyalty or better service quality.

## Summary
**Churned Customers**

- **Numerical:** Higher usage/charges (Total Day Minutes ~210 vs. 180, Charge ~$35 vs. $30; Intl Minutes ~12 vs. 10, Charge ~$3.2 vs. $2.7); more customer service calls (~2–2.5 vs. 1.5); lower voicemail usage (~5 vs. 8–10 messages).
- **Categorical:** 30.4% have international plan (churn rate 44.5%); 16.8% have voice mail plan (churn rate 17.2% without); evenly distributed across area codes (churn rates ~14.5%–15.2%); more in high-churn states (NJ ~50%, TX ~25%).

**Non-Churned Customers**

- **Numerical:** Lower usage/charges (Day Minutes ~180, Charge ~$30; Intl Minutes ~10, Charge ~$2.7); fewer service calls (~1.5); higher voicemail usage (~8–10 messages).
- **Categorical:** 6.7% have international plan (churn rate 11.6% without); 29.3% have voice mail plan (churn rate 9.2%); evenly distributed across area codes; more in low-churn states (HI ~5%, AK ~5%).
----
**Key Observations**

- **Cost Sensitivity:** Higher usage/charges drive churn (bill shock).
- **Service Issues:** More service calls signal dissatisfaction in churned customers.
- **Engagement:** Churned customers use voicemail less, international plans more.
- **Regional Impact:** High churn in NJ, TX; low in HI, AK.
- **Plan Impact:** International plans increase churn (44.5%); voice mail plans reduce it (9.2% vs. 17.2%).

# Which ML models can be implemented, and what are their results?

## Data Exploration & Preprocessing

### EDA:
#### Distribution of Churn
<img src = "Images/churn.png">
As can be seen that, there is a significant imbalance between churn and not churn. Therefore, in order to make the models interpret the most clearly, I would use `SMOTE` to upsample train sets.

#### Check Missing Values
There are mo missing

#### Outliers
<img src = "Images/outliers.png">
Although there are outliers in some features, I knew that this is customer information, therefore the fact that each individual has the unique value of each features is unavoidable and common. So, I kept these outliers to maintain the variety of dataset and help models to learn specific customers.

#### Correlation Heatmap
<img src = "Images/corr.png">

- Most features have low correlation with each other (values close to 0), indicating little multicollinearity.
- Some features are perfectly correlated (correlation = 1), such as:
    - `Total day minutes` and `Total day charge`
    - `Total eve minutes` and `Total eve charge`
    - `Total night minutes` and `Total night charge`
    - `Total intl minutes` and `Total intl charge` These pairs represent the same information in different units.
- `Churn` has the highest positive correlation with`Customer service calls` (0.20) and `Total day minutes` (0.20), suggesting these features are important predictors of churn.
- `Number vmail messages` has a negative correlation with `Churn` (-0.09), indicating customers with more voicemail messages are less likely to churn.

### Feature Engineering:
From previous EDA, I knew that `Total day minutes`, `Total day charge`, `Customer service calls` had the strongest correlation with target. Therefore, I will enhance these features by adding squared values of these.

### Scaling:
StandardScaler applied to numerical features to make all features in equal units, also to reduce skewness and outliers. Also, all features have normal distribution therefore, Standard Scaling is the best option.
### Handling Imbalance:
Used SMOTE to balance the churn classes in the training set.
<img src ="Images/balance.png">

### Feature Selection

#### **Numerical:** 
ANOVA test and correlation analysis to select significant features. In this case, I realized target is categorical and the best option to see the score of numerical features between target is ANOVA.
<img src = "Images/anova.png">

**Features to Choose**
- **Significant Features (P-Value < 0.05):**

    - Customer service calls: Highly significant (P-Value < 0.05) and has a strong correlation with Churn (0.20).
    - Total day minutes: Significant (P-Value < 0.05) and has a strong correlation with Churn (0.20).
    - Number vmail messages: Significant (P-Value < 0.05) and provides unique information (low correlation with other features).
- **Remove Redundant Features:**

    - From the correlation matrix, features like Total day charge, Total eve charge, Total night charge, and Total intl charge are perfectly correlated with their respective "minutes" features. Keep only the "minutes" features:
        - Keep Total day minutes (drop Total day charge).
        - Keep Total eve minutes (drop Total eve charge).
        - Keep Total night minutes (drop Total night charge).
        - Keep Total intl minutes (drop Total intl charge).
- **Drop Insignificant Features (P-Value ≥ 0.05):**

    - Features like Area code, Total eve calls, Total night calls, and Total intl calls have high P-Values and are not significant predictors of Churn.
---
**Final Selected Features**

- Customer service calls
- Total day minutes
- Number vmail messages
- Total eve minutes
- Total night minutes
- Total intl minutes
- Account length (optional, as it has a moderate P-Value but may still provide useful information)

#### **Categorical:** 
Chi-square test to select important categorical variables.
<img src = "Images/chi2.png">

From the p-val and chi score, it is easy to remove Area code.

### Data Oversampling
Since from the previous EDA, I knew that target feature are imbalanced, so I used SMOTE to create the balanced dataset for models to learn.

<img src = "Images/balance.png">

### Modeling
- First of all, we chose ensemble and gradient boosting since these are the most powerful models and time-efficient.
- Also to hyper-tune, I used **Optuna**, instead of GridSearchCV or RandomSearch because these methods are time-consuming.

- Four models were trained and evaluated:
    - Decision Tree
    - Random Forest
    - XGBoost
    - LightGBM


### Evaluation
- **Primary Metric: F1-Score**
    - Balances precision and recall, ensuring the model doesn’t overly sacrifice one for the other.
    Directly focuses on the minority class (Churn) performance, which is critical for churn prediction.
    - Addresses the business need to identify churners (high recall) while ensuring predicted churners are reliable (high precision).

- **Secondary Metric: Recall for Churn**
    - Missing churners (false negatives) is costly for MCI, as it means losing customers without intervention.
    - Recall directly measures the proportion of actual churners identified, aligning with the goal of maximizing churn detection.
#### Metrics
F1-Score (primary), Accuracy, Precision, Recall, Specificity, AUC.
<img src = "Images/metrics.png">

**Best Model:** LightGBM stands out with the second highest F1-Score (0.811) and precision (0.833), closely followed by XGBoost (F1-Score 0.815, precision 0.819). Random Forest excels in recall (0.821), making it the best for capturing churners, while Decision Tree underperforms across all metrics.

**Metric Performance:**
- **F1-Score:** XGBoost (0.815) is the highest, with LightGBM (0.811) very close, both reflecting strong balance for the Churn class.
- **Recall:** Random Forest (0.821) leads, ensuring the most churners are identified, followed by XGBoost (0.811) and LightGBM (0.789).
- **Precision:** LightGBM (0.833) is the most reliable, minimizing false positives, followed by XGBoost (0.819).
- **Accuracy:** High across all models (0.918–0.948), with LightGBM and XGBoost at the top (0.948).
- **Implication:** For MCI, LightGBM offers the best overall performance (highest precision and accuracy), while XGBoost provides the best F1-Score, and Random Forest’s high recall ensures maximum churn detection. The squared features likely contribute to these gains, though their specific impact would require a comparison with a baseline model.

#### Confusion Matrix
<img src = "Images/conf.png">

**Precision (minimizing false positives):** LightGBM and XGBoost perform the best, with the lowest false positives.

**Recall (minimizing false negatives):** Random Forest has the highest recall, capturing the most churners (78 true positives).

**Overall Best Model:**
- LightGBM offers the best balance between precision and recall, with the highest true negatives and competitive true positives.
- Random Forest is better if recall (capturing churners) is prioritized.

#### ROC
<img src = "Images/roc.png">
**Best Models:** XGBoost and LightGBM are the best-performing models with an AUC of 0.90. Both models are highly effective at distinguishing between churners and non-churners.

**Intermediate Performance:** Random Forest performs well with an AUC of 0.89 but is slightly less effective than XGBoost and LightGBM.

**Least Effective Model:** Decision Tree has the lowest AUC (0.88), indicating weaker performance compared to the other models.

# What features are most important for predicting churn?
<img src = "Images/importances.png">

1. **What is Feature Importance in LightGBM?**
- Feature importance in LightGBM measures how much each feature contributes to the model’s predictions. LightGBM typically uses:

    - **Gain:** The reduction in the loss function (e.g., binary log-loss for churn prediction) attributed to splits on a feature across all trees. This is the default metric and reflects the most significant contributors to model accuracy.
    - **Split Count:** The number of times a feature is used to split the data, indicating its frequency of use.
    - **Cover:** The average coverage of samples affected by splits on a feature, weighted by the number of observations.

2. **Explain Feature Importance**
- **Top Features:**

    - **Total intl minutes:** The most important feature, indicating that international call usage strongly correlates with churn. Customers with high international usage may face higher costs, leading to dissatisfaction.
    - **Total night minutes:** Nighttime call usage is the second most important feature. High usage here may indicate specific customer behavior patterns.
    - **Customer service calls:** High importance suggests that frequent customer service interactions are a strong indicator of dissatisfaction and potential churn.
    - **Total eve minutes and Total day minutes:** Evening and daytime call usage also play significant roles, likely reflecting overall engagement with the service.

- **Moderately Important Features:**

    - **Account length:** Indicates customer tenure. Shorter tenure may correlate with higher churn, as newer customers are less loyal.
    - **Total day minutes_squared and Total day charge_squared:** These engineered features capture non-linear relationships, showing that extreme usage patterns (e.g., very high charges) may drive churn.
- **Less Important Features:**

    - **Number vmail messages:** Indicates voicemail usage. Lower usage may suggest disengagement with value-added services.
    - **Voice mail plan and International plan:** While less important, these features still provide insights into customer preferences and behaviors.
###  Insights

- **Top churn drivers:** High international minutes, high night minutes, frequent customer service calls.
- **Best model:** LightGBM (highest F1-Score and precision).
- **Actionable recommendations:** Target high-risk customers, address service issues, and promote value-added services.

# What actions regarding qualitative and quantitative analytics could be implemented to enhance retention rate?
## Quantitative Analytics Actions
These use data-driven insights from the model.

### Segment High-Risk Customers Using Model Predictions:
- **Insight:** LightGBM’s high accuracy (0.948) and F1-Score (0.811) suggest reliable churn predictions.
- **Action:** Predict churn probabilities for all customers using LightGBM (predict_proba). Segment into:
    - High Risk: Probability > 0.7.
    - Medium Risk: 0.3–0.7.
    - Low Risk: < 0.3.
- Target high-risk customers with retention offers (e.g., discounts). If ~100 customers are high-risk, retaining 40 (40% success) could save $40,000 (assuming $1,000/customer lifetime value).
### Target Customers with High International Usage:
- **Insight:** Total intl minutes is the top feature (~300), indicating international usage drives churn (e.g., high costs or poor service).
- **Action:** Identify customers with >50 intl minutes/month and high risk (probability > 0.5). Offer discounted international rates or bundled plans. If 200 customers fit this profile, retaining 50 (25% success) could save $50,000.
### Address High Night Usage:
- **Insight:** Total night minutes (~250) suggests night usage patterns influence churn, possibly due to overage charges.
- **Action:** Analyze night usage (>200 minutes) for high-risk customers. Offer unlimited night plans for $5/month. If 150 customers qualify, retaining 30 (20% success) could save $30,000.
### Reduce Customer Service Calls:
- **Insight:** Customer service calls (~250) indicates dissatisfaction (churners average 2.2 calls vs. 1.4).
- **Action:** Target customers with ≥3 calls in 3 months and high risk. Provide proactive support (e.g., account manager). If 200 customers have ≥3 calls, retaining 60 (30% success) could save $60,000.
### Encourage Voice Mail Usage:
- **Insight:** Number vmail messages (~100) and Voice mail plan (~80) suggest lower usage among churners (~5 vs. 8–10).
- **Action:** Offer free voicemail trials to high-risk customers without a plan. If 300 lack a plan, targeting 100 high-risk ones might retain 15 (15% adoption, 50% success), saving $15,000.

## Qualitative Analytics Actions
These gather customer feedback to understand the “why” behind churn.

### Survey International Users:
- **Insight:** Total intl minutes’s high importance suggests international usage issues.
- **Action:** Survey customers with >50 intl minutes (e.g., “Why do you churn?”). If 50% cite high costs, introduce competitive rates, potentially retaining 20 of 100 high-risk users ($20,000 saved).
### Interview High Night Usage Customers:
- **Insight:** Total night minutes may reflect cost or service issues.
- **Action:** Interview customers with >200 night minutes to identify concerns (e.g., overage fees). If 30% report costs, offer tailored plans, retaining 10 of 50 high-risk users ($10,000 saved).
### Gather Feedback on Service Calls:
- **Insight:** Customer service calls signals dissatisfaction.
- **Action:** Survey customers with ≥3 calls (e.g., “What’s your issue?”). If 40% cite billing errors, improve billing clarity, retaining 20 of 100 high-risk users ($20,000 saved).
### Explore Voice Mail Barriers:
- **Insight:** Low Number vmail messages and Voice mail plan usage among churners.
- **Action:** Interview customers with <5 messages to understand barriers (e.g., complexity). Simplify setup, retaining 10 of 50 high-risk users ($10,000 saved).
### Conduct Exit Interviews:
- **Insight:** Model predicts who, but not why.
- **Action:** Survey churned customers (e.g., “Why did you leave?”). If 50% cite service, enhance support, reducing churn by 10% (39 customers, $39,000 saved annually).
---
# How to Run

1. Install dependencies:
    ```sh
    pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn xgboost lightgbm optuna
    ```
2. Place the CSV files in the project directory.
3. Open and run [test.ipynb](test.ipynb) in Jupyter or VS Code.

## Files

- `test.ipynb`: Main analysis and modeling notebook.
- `Copy of churn-bigml-80.csv`: Training data.
- `Copy of churn-bigml-20.csv`: Test data.

## Results

- **LightGBM** achieved the best performance with an F1-Score of ~0.81 and AUC of ~0.90.
- Feature importance and actionable business recommendations are provided in the notebook.

---

**Author:**  
- Trương Thuận Kiệt

**Contact:**  
- Gmail: truongthuankiet1990@gmail.com