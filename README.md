# 🐷 Anomaly Detection in Livestock Activity

> **[ETRI]** Study of anomaly detection about the symptoms animals exhibit, based on activity data, for early disease detection.  
> 가축 질병 조기 탐지를 위한 이상치 데이터 분석 연구

> ⚠️ **Note:** The original research data and code are confidential. This repository contains a rewritten version of the study for portfolio purposes.

---

## 📌 Overview

This project detects anomalies in pig activity data to identify early signs of disease after vaccination. By analyzing activity degradation patterns using the **ADTK** library, the study aims to pinpoint the onset of abnormal behavior as early as possible.

---

## 🔬 Research Background

| Item | Detail |
|------|--------|
| **Organization** | ETRI (Electronics and Telecommunications Research Institute) |
| **Period** | November 4, 2022 ~ November 7, 2022 |
| **Team Size** | 1 person |
| **IDE** | Jupyter Notebook |
| **Data Source** | Pig experiment data provided by a university (April 10 ~ April 29, 2021) |

### Experiment Data

| Dataset | Vaccination Date | Pathogen |
|---------|-----------------|---------|
| Data A | 2021.04.22 | Bacteria A |
| Data B | 2021.04.15 | Virus B |

---

## 🎯 Objective

Using the **ADTK (Anomaly Detection Toolkit)**, detect the activity degradation sections in Data A and Data B after vaccination — identifying the earliest possible signs of disease onset.

---

## 🔄 Process

**1. Data Collection**
- Extracted pig activity from image data using **OpenCV**
- Constructed activity DataFrames per pig per time unit

**2. Data Preprocessing**
- Replaced values exceeding the **Upper Middle Line (UML)** with zero to remove noise

**3. Data Analysis & Visualization**
- Modified the algorithm of ADTK's `persistAD` function:
  ```
  Original : aggregate(DRA) → anomaly detection
  Modified : aggregate(DRA) → resample → anomaly detection
  ```
- Applied various time windows (`1h`, `12h`, etc.) to `DRA` and `resample` functions
- Framed detected anomaly sections into DataFrames
- Visualized activity data alongside detected anomalies
- Repeated the process across multiple window configurations

**4. Evaluation**
- Calculated **Accuracy**, **Precision**, and **Recall** for each configuration
- Selected the **Top 10 cases** for Data A and Data B based on Precision and Recall (20 cases total)
- Took the **intersection** of the top 10 cases from each dataset
- Presented graphs for the **best-performing cases**

---

## 📊 Evaluation Metrics

| Metric | Description |
|--------|-------------|
| Accuracy | Overall correctness of anomaly detection |
| Precision | How many detected anomalies were actually anomalies |
| Recall | How many actual anomalies were detected |

> Priority was given to **Precision and Recall** over Accuracy, as missing a disease onset (false negative) is more critical than a false alarm.

---

## 🛠️ Tech Stack

- **Language:** Python 3
- **Libraries:** ADTK, OpenCV, Pandas, Matplotlib
- **IDE:** Jupyter Notebook

---

## 📁 Repository Structure

```
anomalyDetection/
├── 01capturing.md           # Data collection process
├── 02makeDFndataPro.md      # DataFrame creation & preprocessing
├── 03dataAnalysis.md        # Analysis & visualization
├── 04evaluating.md          # Evaluation results
├── README.md
└── 이상징후조기감지를위한활동성기반가축이상탐지연구.pdf  # Full research paper (Korean)
```

---

## 🔒 Security

The original source code and raw data are confidential per ETRI's data policy. This repository contains a rewritten documentation-based version of the study.
