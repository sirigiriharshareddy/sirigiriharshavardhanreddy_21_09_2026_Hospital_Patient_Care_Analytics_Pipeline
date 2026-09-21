# 🏥 Hospital Patient Care Analytics Pipeline

> A data-driven healthcare analytics project focused on understanding patient flow, waiting time, admission patterns, demographics, and patient satisfaction.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Processing-150458?logo=pandas)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange)
![Seaborn](https://img.shields.io/badge/Seaborn-Analytics-4C72B0)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter)
![Status](https://img.shields.io/badge/Status-Academic%20Project-success)

---

## 📌 Project Overview

Hospitals generate data through patient registration, admissions, department referrals, waiting-time records, and satisfaction surveys. When this information is not analyzed systematically, it becomes difficult to identify operational bottlenecks and understand patient experience.

This project implements a **Hospital Patient Care Analytics Pipeline** using a Kaggle healthcare patient-flow dataset. The workflow demonstrates how raw healthcare data can be:

1. Ingested from a CSV file
2. Inspected and validated
3. Cleaned and transformed
4. Analyzed using healthcare-focused KPIs
5. Visualized through charts
6. Exported into dashboard-ready summary files

The project follows the stages described in the assignment:

> **Data Ingestion → Data Processing → Data Storage/Export → Analytics → Dashboard-Ready Outputs**

---

## 🎯 Project Objectives

- Analyze hospital patient-flow data.
- Identify patterns in patient waiting time.
- Compare waiting time across department referrals.
- Study admission and non-admission patterns.
- Analyze patient demographics.
- Examine the relationship between waiting time and satisfaction.
- Perform data-quality checks for missing and duplicate records.
- Generate cleaned datasets and analytical summary tables.
- Prepare outputs that can be used in a BI dashboard.

---

## 🧱 System Architecture

```text
                 ┌─────────────────────────────┐
                 │      Kaggle CSV Dataset     │
                 │ Patient Flow Records        │
                 └──────────────┬──────────────┘
                                │
                                ▼
                 ┌─────────────────────────────┐
                 │       Data Ingestion        │
                 │       Pandas read_csv       │
                 └──────────────┬──────────────┘
                                │
                                ▼
                 ┌─────────────────────────────┐
                 │   Data Inspection & Quality │
                 │ Missing Values / Duplicates │
                 └──────────────┬──────────────┘
                                │
                                ▼
                 ┌─────────────────────────────┐
                 │    Data Cleaning & ETL      │
                 │ Type Conversion             │
                 │ Missing Value Handling      │
                 │ Feature Engineering         │
                 └──────────────┬──────────────┘
                                │
                                ▼
                 ┌─────────────────────────────┐
                 │       Analytics Layer       │
                 │ Waiting Time                 │
                 │ Admission Patterns          │
                 │ Demographics                 │
                 │ Satisfaction                 │
                 └──────────────┬──────────────┘
                                │
                                ▼
                 ┌─────────────────────────────┐
                 │ Visualization & Export      │
                 │ Charts / CSV Summary Files   │
                 └─────────────────────────────┘
```

---

## 📊 Dataset Information

**Dataset:** Healthcare Analytics – Patient Flow Dataset  
**Source:** Kaggle  
**Records:** 9,216  
**Columns:** 11  
**File:** `healthcare_analytics_patient_flow_data.csv`

### Dataset Attributes

| Column | Description |
|---|---|
| `Patient Id` | Patient identifier |
| `Patient Admission Date` | Date of patient admission/visit |
| `Patient Admission Time` | Time of patient admission/visit |
| `Merged` | Additional record field present in the source dataset |
| `Patient Gender` | Patient gender |
| `Patient Age` | Patient age |
| `Patient Race` | Patient race category |
| `Department Referral` | Department referred to |
| `Patient Admission Flag` | Admission or non-admission status |
| `Patient Satisfaction Score` | Satisfaction score |
| `Patient Waittime` | Patient waiting time in minutes |

> **Privacy note:** The dataset is intended for educational analytics. Patient identifiers should be masked or removed before any real-world deployment.

---

## 🛠️ Technologies Used

- **Python** – Core programming language
- **Pandas** – Data ingestion, cleaning, transformation, and aggregation
- **NumPy** – Numerical operations
- **Matplotlib** – Data visualization
- **Seaborn** – Statistical visualization
- **Jupyter Notebook** – Interactive execution and documentation
- **CSV** – Input and output data format

---

## 🔄 Data Processing Workflow

### 1. Data Ingestion

- Load the CSV file using Pandas.
- Display dataset dimensions and sample records.
- Inspect column names and data types.

### 2. Data Quality Assessment

- Check missing values.
- Check duplicate rows.
- Check duplicate patient identifiers.
- Inspect categorical values.
- Validate age, waiting time, and satisfaction ranges.

### 3. Data Cleaning

- Standardize column names.
- Convert date fields into datetime format.
- Handle missing categorical values.
- Handle missing satisfaction scores using a documented strategy.
- Convert numerical columns into suitable data types.
- Remove invalid age and waiting-time records.
- Remove exact duplicate rows.

### 4. Feature Engineering

The following analytical fields are created:

- `age_group`
- `wait_time_category`
- `satisfaction_category`

These fields make the dataset easier to analyze and visualize.

---

## 📈 Analytics Implemented

### Hospital Key Performance Indicators

- Total patient records
- Average waiting time
- Median waiting time
- Maximum waiting time
- Average satisfaction score
- Admission rate

### Waiting-Time Analysis

- Department-wise patient count
- Average waiting time by department
- Median waiting time by department
- Maximum waiting time by department
- Waiting-time distribution

### Patient Demographics

- Patient distribution by age group
- Gender-wise patient summary
- Race-wise patient distribution
- Average age by gender

### Admission Analysis

- Admission versus non-admission counts
- Admission status by department
- Department-wise admission percentage

### Patient Satisfaction Analysis

- Satisfaction score distribution
- Average satisfaction by waiting-time category
- Comparison of patient waiting time and satisfaction

---

## 📊 Visualizations

The notebook generates visualizations for:

1. Distribution of patient waiting time
2. Average waiting time by department
3. Patient admission status
4. Patient distribution by age group
5. Patient satisfaction score distribution
6. Average satisfaction by waiting-time category
7. Admission status percentage by department

These visualizations help identify operational patterns and support hospital-management reporting.

---

## 🗂️ Generated Output Files

After running the notebook, the following files are generated:

| Output | Purpose |
|---|---|
| `hospital_patient_flow_cleaned.csv` | Cleaned and transformed dataset |
| `department_waiting_time.csv` | Department-level waiting-time metrics |
| `admission_by_department.csv` | Admission distribution by department |
| `wait_time_vs_satisfaction.csv` | Waiting-time and satisfaction analysis |
| `gender_summary.csv` | Gender-wise analytics |
| `race_summary.csv` | Race-wise patient counts |

---

## 🏢 Data Warehouse Design Proposal

A production-ready hospital analytics platform can use a star schema.

### Fact Tables

- `Fact_Patient_Visit`
- `Fact_Appointment`
- `Fact_Treatment`
- `Fact_Lab_Result`

### Dimension Tables

- `Dim_Patient`
- `Dim_Doctor`
- `Dim_Department`
- `Dim_Date`
- `Dim_Hospital_Location`

The current dataset primarily supports patient-flow analytics. Additional source systems would be required to populate laboratory, wearable-device, doctor-note, and treatment-specific fact tables.

---

## 🔐 Security and Privacy Considerations

Healthcare information is sensitive. A real-world implementation should include:

- Encryption at rest and during transmission
- Role-based access control
- Authentication and authorization
- Patient identifier masking or tokenization
- Audit logs
- Data retention policies
- Backup and disaster recovery
- Restricted access for authorized hospital staff only

This academic project uses a CSV-based workflow and does not represent a production clinical system.

---

## 🤖 Machine Learning Scope and Limitation

The assignment mentions patient risk analysis and classification. However, the selected dataset does not provide a clinically validated high-risk patient label and does not contain complete clinical variables such as laboratory results, wearable readings, or doctor consultation notes.

Therefore:

- The current implementation focuses on descriptive and operational analytics.
- A medical risk-prediction model is not claimed from the available fields.
- A future ML extension would require an appropriate target label, relevant clinical features, validation, and clinical oversight.
- Any model should support—not replace—professional medical decision-making.

---

## 🚀 Future Enhancements

The project can be extended with:

- Real-time ingestion using Apache Kafka
- Batch ingestion from hospital databases
- Data lake storage using AWS S3 or an equivalent platform
- Data warehouse implementation using PostgreSQL or another warehouse
- Dashboard development using Power BI, Tableau, or Streamlit
- Pipeline orchestration using Apache Airflow
- Data-quality monitoring and automated alerts
- Integration of laboratory and wearable-device data
- De-identified clinical risk-analysis datasets
- Role-based access and audit logging

---

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Keep the files together

```text
project-folder/
│
├── Hospital_Patient_Care_Analytics_Completed.ipynb
├── healthcare_analytics_patient_flow_data.csv
└── README.md
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open the notebook and select:

```text
Run → Run All Cells
```

---

## ⚠️ Important Dataset Limitation

The assignment describes multiple hospital data sources, including:

- Patient registration
- Appointments
- Laboratory reports
- Wearable devices
- Doctor consultation notes
- Pharmacy and billing

The selected Kaggle dataset does not contain all these sources. The implemented notebook therefore demonstrates the supported patient-flow and operational analytics components, while the remaining components are documented as architecture and future-extension proposals.

No unsupported clinical results or risk labels are fabricated.

---

## 👨‍🎓 Academic Project

**Project:** Hospital Patient Care Analytics Pipeline  
**Domain:** Healthcare Data Engineering and Analytics  
**Dataset:** Kaggle Healthcare Analytics – Patient Flow Dataset  
**Implementation:** Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook

---

## 📄 Conclusion

This project demonstrates how healthcare patient-flow data can be transformed into meaningful operational insights through data ingestion, quality validation, cleaning, feature engineering, analytics, visualization, and exportable reporting tables.

The pipeline supports analysis of waiting time, admission patterns, patient demographics, and satisfaction, while clearly identifying the additional data and infrastructure required for a complete hospital-wide production system.
