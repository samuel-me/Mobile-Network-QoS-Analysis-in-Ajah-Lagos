# Network Quality of Service (QoS) Analysis

A data-driven analysis of MTN Nigeria's 3G network signal quality using real drive test data collected across multiple days and sessions. This project processes, classifies, and visualizes key radio frequency (RF) metrics to assess network performance across geographic locations.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Metrics Analyzed](#metrics-analyzed)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Signal Classification Standards](#signal-classification-standards)
- [Visualizations](#visualizations)
- [Results](#results)
- [Technologies Used](#technologies-used)

---

## 🔍 Overview

This project analyzes drive test data collected from MTN Nigeria's 3G network. Drive testing is a standard telecommunications practice where signal measurements are recorded while moving through a coverage area. The goal is to assess the **Quality of Service (QoS)** by evaluating three core RF metrics:

- **Ec/Io** — Signal quality (carrier-to-interference ratio)
- **Rx Power** — Received signal strength
- **RSCP** — Received Signal Code Power

Each metric is classified into quality categories (Very Good → Very Poor) using industry-standard thresholds, then visualized on interactive maps, count plots, and distribution charts.

---

## 📂 Dataset

| Field | Description |
|---|---|
| `Time` | Timestamp of measurement |
| `Date` | Date of measurement (collected July 2024) |
| `Latitude` | GPS latitude coordinate |
| `Longitude` | GPS longitude coordinate |
| `Events` | Network event type (e.g., Idle Mode) |
| `Rx Power (dBm)` | Received signal power in decibels-milliwatts |
| `Agg. Active Ec/Io (dB)` | Aggregate active Ec/Io in decibels |
| `Agg. Active RSCP (dBm)` | Aggregate active RSCP in decibels-milliwatts |

> **Coverage Area:** Coordinates around latitude 6.46°N, longitude 3.56°E (Lagos/Ogun area, Nigeria)

> **Sessions:** Data is split into **Morning** (before 3PM) and **Evening** sessions, and grouped by **Day of the Week** for temporal analysis.

---

## 📊 Metrics Analyzed

### 1. Ec/Io (Signal Quality)
Measures the ratio of the pilot channel energy to total interference. A key indicator of signal quality in CDMA/WCDMA networks.

### 2. Rx Power (Received Signal Strength)
Measures the total received power at the device. Indicates how strong the signal is at any given location.

### 3. RSCP (Received Signal Code Power)
Measures the power of the received pilot channel. Used to determine coverage and handover decisions.

---

## 🗂️ Project Structure

```
MTN-QoS-Analysis/
│
├── MTN.ipynb              # Main analysis notebook
├── ms2.xlsx               # Raw drive test data (input)
├── ms2_Ecio.csv           # Processed Ec/Io data with classifications
├── ms2_RxPower.csv        # Processed Rx Power data with classifications
├── ms2_Rscp.csv           # Processed RSCP data with classifications
├── map.html               # Interactive Folium route map
└── README.md              # Project documentation
```

---

## ⚙️ Installation

1. **Clone the repository:**
```bash
git clone https://github.com/yourusername/mtn-qos-analysis.git
cd mtn-qos-analysis
```

2. **Install required dependencies:**
```bash
pip install pandas numpy seaborn matplotlib plotly folium openpyxl
```

3. **Launch Jupyter Notebook:**
```bash
jupyter notebook MTN.ipynb
```

---

## 🚀 Usage

1. Place your drive test Excel file in the project directory and update the filename:
```python
name = 'ms2'  # Change to your file name (without .xlsx)
data = pd.read_excel(name + '.xlsx')
```

2. Run all cells in `MTN.ipynb` sequentially.

3. Processed CSV files and visualizations will be generated automatically.

---

## 📏 Signal Classification Standards

### Ec/Io Classification
| Category | Ec/Io Range (dB) |
|---|---|
| Very Good | ≥ -8 |
| Good | -12 to -9 |
| Fair | -16 to -13 |
| Poor | -20 to -17 |
| Very Poor | ≤ -21 |

### Rx Power Classification
| Category | Rx Power Range (dBm) |
|---|---|
| Excellent | ≥ -50 |
| Very Good | -70 to -50 |
| Good | -85 to -70 |
| Fair | -100 to -85 |
| Poor | < -100 |

### RSCP Classification
| Category | RSCP Range (dBm) |
|---|---|
| Very Good | ≥ -60 |
| Good | -75 to -61 |
| Fair | -85 to -76 |
| Poor | -95 to -86 |
| Very Poor | -124 to -96 |

---

## 📈 Visualizations

The notebook generates the following visualizations for each metric:

1. **Interactive Route Map** — Folium/Plotly map showing the drive test route with color-coded signal quality markers
2. **Count Plot** — Distribution of signal quality categories across the dataset
3. **Distribution Plot** — Statistical distribution of raw signal values

Color coding used across all maps:
| Quality | Color |
|---|---|
| Very Good / Excellent | 🟢 Green |
| Good | 🔵 Blue |
| Fair | 🟡 Orange/Gold |
| Poor | 🔴 Red |
| Very Poor | 🟥 Dark Red |

---

## 🏁 Results

The analysis provides:
- A **geospatial view** of network quality across the drive test route
- **Temporal insights** by session (Morning vs. Evening) and day of the week
- **Statistical summaries** of each RF metric including mean, min, max, and standard deviation
- **Quality category breakdowns** showing the percentage of time spent in each signal quality band

---

## 🛠️ Technologies Used

| Tool | Purpose |
|---|---|
| Python 3 | Core programming language |
| Pandas | Data loading, cleaning, and processing |
| NumPy | Numerical computations |
| Matplotlib & Seaborn | Static visualizations |
| Plotly Express | Interactive map visualizations |
| Folium | Route map generation |
| Jupyter Notebook | Interactive development environment |


This project is for academic and research purposes. Data belongs to the respective network operator.
