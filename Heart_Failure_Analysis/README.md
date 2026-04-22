# Heart Failure Prediction

## Project Overview
This project focuses on building a machine learning model to predict heart disease based on various clinical parameters. The primary goal is to leverage data analysis and predictive modeling to identify individuals at risk, aiding in early detection and intervention.

## Dataset
The dataset used for this project is the "Heart Failure Prediction" dataset, sourced from Kaggle. It contains 11 features that describe a patient's health status and one target variable indicating the presence or absence of heart disease.

**Features include:**
*   `Age`: Age of the patient
*   `Sex`: Sex of the patient (M/F)
*   `ChestPainType`: Type of chest pain (TA, ATA, NAP, ASY)
*   `RestingBP`: Resting blood pressure
*   `Cholesterol`: Serum cholesterol
*   `FastingBS`: Fasting blood sugar (1 if > 120 mg/dl, 0 otherwise)
*   `RestingECG`: Resting electrocardiogram results (Normal, ST, LVH)
*   `MaxHR`: Maximum heart rate achieved
*   `ExerciseAngina`: Exercise-induced angina (Y/N)
*   `Oldpeak`: Previous peak (ST depression induced by exercise relative to rest)
*   `ST_Slope`: The slope of the peak exercise ST segment
*   `HeartDisease`: Target variable (1 if heart disease, 0 if no heart disease)

## Exploratory Data Analysis (EDA)
Comprehensive EDA was performed to understand the data distribution, identify patterns, and uncover relationships between variables. Key insights include:

*   **Age Trends**: A clear increase in the prevalence of heart disease was observed in older age groups, with average resting blood pressure and 'Oldpeak' also increasing with age, while maximum heart rate generally decreased.
*   **Sex Differences**: Males showed a higher incidence of heart disease in the dataset. Females tended to have higher average cholesterol and maximum heart rates, while males had higher average 'RestingBP' and 'Oldpeak'.
*   **Chest Pain Type**: 'ASY' (Asymptomatic) chest pain was strongly correlated with the presence of heart disease, whereas 'ATA' (Typical Angina) and 'NAP' (Non-Anginal Pain) were more frequently associated with no heart disease.

## Data Preprocessing

The following preprocessing steps were carried out:
*   **Outlier Detection and Handling**: IQR-based outlier detection was applied to numerical features. Specific data points identified as medically inaccurate (e.g., `RestingBP < 90`, `Cholesterol == 0`) were removed to improve data quality.
*   **Feature Engineering**: A new categorical feature `Age_Range` was created by binning the `Age` column into 10-year intervals to better analyze age-related trends.
*   **Categorical Encoding**: Categorical features (`Sex`, `ChestPainType`, `RestingECG`, `ExerciseAngina`, `ST_Slope`) were converted into numerical format using one-hot encoding (`pd.get_dummies`) for compatibility with the machine learning model.

## Machine Learning Model

A **Random Forest Classifier** was chosen for its robustness and ability to handle complex datasets. The dataset was split into training and testing sets (80% train, 20% test) to evaluate model performance.

### Model Performance

*   **Training Accuracy**: 1.0 (indicating the model learned the training data perfectly)
*   **Test Accuracy**: 0.91 (91% of predictions on unseen data were correct)

### Detailed Classification Metrics:

| Class | Precision | Recall | F1-Score | Support |
| :---- | :-------- | :----- | :------- | :------ |
| 0     | 0.87      | 0.94   | 0.91     | 71      |
| 1     | 0.95      | 0.87   | 0.91     | 79      |
| **Accuracy** |           |        | **0.91** | **150** |
| **Macro Avg** | 0.91      | 0.91   | 0.91     | 150     |
| **Weighted Avg** | 0.91      | 0.91   | 0.91     | 150     |

### Confusion Matrix

|          | Predicted No (0) | Predicted Yes (1) |
| :------- | :--------------- | :---------------- |
| **Actual No (0)** | 67 (True Negative) | 4 (False Positive) |
| **Actual Yes (1)** | 10 (False Negative) | 69 (True Positive) |


**Insights from Metrics:**
*   **High Precision for Heart Disease (Class 1)**: When the model predicts heart disease, it is correct 95% of the time, which is valuable in medical screening to minimize false alarms.
*   **Good Recall for Heart Disease (Class 1)**: The model identified 87% of all actual heart disease cases. The 13% false negatives (patients with heart disease missed by the model) highlight a critical area for potential improvement, as minimizing these is paramount in medical diagnosis.
*   **Balanced F1-Score**: The F1-score of 0.91 for both classes indicates a good balance between precision and recall.

## How to Run the Notebook

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd heart-failure-prediction
    ```
2.  **Set up the environment:**
    Ensure you have Python installed. It's recommended to use a virtual environment.
    ```bash
    python -m venv venv
    source venv/bin/activate # On Windows use `venv\Scripts\activate`
    pip install -r requirements.txt # (Assuming you create a requirements.txt from your environment)
    ```
3.  **Install Dependencies:**
    The project relies on libraries such as `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, and `kagglehub`. You can install them using pip:
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn kagglehub
    ```
4.  **Run the Jupyter Notebook:**
    Open the `Heart_Failure_Prediction.ipynb` (or similar name) notebook in a Jupyter environment (e.g., Jupyter Lab, VS Code with Jupyter extension, Google Colab).
    ```bash
    jupyter notebook
    ```
