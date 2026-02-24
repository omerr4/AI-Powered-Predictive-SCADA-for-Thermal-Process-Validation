
---

```markdown
# AI-Powered Predictive SCADA for Thermal Process Validation

##  Problem Statement
In traditional thermal processing (Retort), process deviations are often detected post-processing through data loggers or incubation tests, leading to significant product waste or food safety risks (e.g., *Clostridium botulinum* survival). 

This project shifts the paradigm from **reactive monitoring** to **proactive prevention** by predicting the final **P-Value (Lethality)** during the early stages of the heating cycle.



---

##  Technical Methodology

### 1. Mechanistic Digital Twin (Data Generation)
The training data is generated via a high-fidelity simulation based on heat transfer physics:
* **Lethality Kinetics:** Calculation of the Accumulated P-Value using the Bigelow method P_ = 93.3C, Z = 8.89.
* **Heat Transfer:** Modeling the core temperature using a dynamic Heat Transfer Coefficient (HTC) that accounts for equipment degradation and thermal fouling.
* **Deviation Injection:** Stochastic modeling of steam supply failures, setpoint errors, and premature cooling cycles.



### 2. Deep Learning Architecture
* **Model Type:** Long Short-Term Memory (LSTM) Recurrent Neural Network.
* **Observation Window:** 40 Minutes of multi-variate time-series data.
* **Architecture:** Dual-stacked LSTM layers with Dropout regularization to prevent overfitting and ensure generalization across different batch conditions.



### 3. Real-time Deployment Pipeline
* **Inference Engine:** TensorFlow / Keras.
* **Backend:** SQLite for live telemetry storage.
* **Frontend:** Streamlit-based SCADA Dashboard for real-time visualization and risk assessment.



---

##  Performance Metrics
The model was validated against a blind test set of **200 industrial batches**, achieving near-perfect separation between safe and deviated processes:

| Metric | Value | Target |
| :--- | :--- | :--- |
| **Accuracy** | **0.97** | > 0.90 |
| **Matthews Correlation (MCC)** | **0.95** | > 0.70 |
| **PR-AUC** | **0.99** | > 0.85 |
| **Brier Score Loss** | **0.019** | < 0.10 |

###  Detailed Classification Report

> **Note:** The model shows exceptional capability in identifying failed batches (Class 1) with high precision, which is critical for food safety.

* **Safe Batch (0):** * Precision: **0.96** | Recall: **0.99** | F1-Score: **0.97**
* **Deviated Batch (1):** * Precision: **0.99** | Recall: **0.96** | F1-Score: **0.98**

---

> [!IMPORTANT]
> **Notice:** The source code and specific architectural weights for this project are proprietary. For a full technical demonstration or access requests for peer review, please contact the repository owner.

```

---



