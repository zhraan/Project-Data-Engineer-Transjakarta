# 🚌 Project Data Engineer — Transjakarta Public Transportation Transaction

## 📋 Overview

Proyek Data Engineering end-to-end menggunakan dataset transaksi TransJakarta dari Kaggle. Proyek ini menerapkan standar **Data Governance**, **Medallion Architecture**, dan **Privacy Policy** untuk menghasilkan data yang bersih, terstruktur, dan siap analisis.

**Dataset**: [Transjakarta Transportation Transaction (Kaggle)](https://www.kaggle.com/datasets/dikisahkan/transjakarta-transportation-transaction)

## 🎯 Objectives

1. **Data Cleansing** & **Data Quality Check** — Membersihkan dan memvalidasi data
2. **Data Governance** & **Medallion Architecture** (Bronze → Silver → Gold)
3. **Privacy Policy** — Masking data sensitif (PII)
4. **Metadata Strategy** — Data Dictionary lengkap
5. **Data Analysis** — Visualisasi dan insight
6. **Export** — Excel (.xlsx) dan SQL (.sql) untuk MySQL

## 🏗️ Architecture

```
Raw Data (CSV)
    │
    ▼
┌──────────────┐
│ 🥉 BRONZE    │ ← Raw data + ingestion metadata
│   Layer      │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ 🥈 SILVER    │ ← Cleansed, validated, PII masked
│   Layer      │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ 🥇 GOLD      │ ← Aggregated, analytics-ready
│   Layer      │
└──────┬───────┘
       │
       ▼
  Export (Excel / SQL)
```

## 📊 Dataset Info

| Info | Detail |
|------|--------|
| Source | Kaggle |
| Rows | 189,500 |
| Columns | 22 |
| Period | 2023 |
| Format | CSV |

## 🔍 Key Processes

### Data Quality Check
- **Completeness** — Missing values analysis
- **Consistency** — Format & value standardization
- **Validity** — Business rule validation
- **Uniqueness** — Duplicate detection

### Privacy Policy (Data Masking)
| Column | PII Type | Masking Method |
|--------|----------|----------------|
| `payCardID` | Card Number | Last 4 digits only (`****5671`) |
| `payCardName` | Passenger Name | First letter only (`A*** S***`) |
| `payCardBirthDate` | Birth Year | Converted to age group |

### Gold Layer Tables
1. **Corridor Summary** — Revenue & transactions per corridor
2. **Hourly Traffic** — Transaction distribution by hour
3. **Demographics** — Statistics by gender & age group
4. **Daily Trend** — Daily transaction trends

## 📈 Visualizations

The notebook includes 9 comprehensive visualizations:
1. Distribusi Transaksi per Jam (Hourly Transaction Distribution)
2. Top 10 Corridor Tersibuk (Busiest Corridors)
3. Distribusi Metode Pembayaran (Payment Method Distribution)
4. Distribusi Jumlah Pembayaran (Payment Amount Distribution)
5. Demografi Penumpang (Passenger Demographics)
6. Trend Transaksi Harian (Daily Transaction Trend)
7. Distribusi Transaksi per Hari (Day-of-Week Distribution)
8. Peta Halte Populer (Popular Stop Map)
9. Heatmap Korelasi (Correlation Heatmap)

## 💡 Key Insights

1. **Commuter Pattern** — Peak transactions at morning (06-09) and evening (17-19) rush hours
2. **Weekday vs Weekend** — Weekday transactions significantly higher than weekends
3. **Demographics** — Majority of passengers are working-age adults
4. **Free Rides** — Significant proportion of Rp 0 transactions (likely subsidized)

## 🛠️ Tech Stack

- **Python** (pandas, numpy, matplotlib, seaborn)
- **Jupyter Notebook**
- **Excel** (openpyxl) for export
- **MySQL** (sqlalchemy) for database export

## 📁 Project Structure

```
├── Project_Data_Engineer_Transjakarta.ipynb  # Main notebook
├── Project_Data_Engineer_Transjakarta.pdf    # PDF export
├── Transjakarta - Public Transportation Transaction/
│   └── dfTransjakarta180kRows.csv            # Raw dataset
├── TransJakarta_Clean_Data.xlsx              # Cleaned data (generated)
├── TransJakarta_Export.sql                   # SQL export (generated)
├── Instruction Project Data Engineer.docx    # Project instructions
└── README.md
```

## 🚀 How to Run

1. Clone this repository
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn openpyxl sqlalchemy pymysql
   ```
3. Open and run the Jupyter Notebook:
   ```bash
   jupyter notebook Project_Data_Engineer_Transjakarta.ipynb
   ```

## 📝 Note

The exported files (`TransJakarta_Clean_Data.xlsx` and `TransJakarta_Export.sql`) are excluded from Git due to their large size. They will be generated when you run the notebook.

---

*Project Data Engineer | Dibimbing*
