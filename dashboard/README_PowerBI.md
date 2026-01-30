# Power BI Fraud Dashboard Instructions

Since `.pbix` files are binary project files created by Power BI Desktop, they cannot be generated manually. However, you can create the dashboard in minutes using the data we generated.

## 1. Get the Data
The project generated a file at:
`outputs/fraud_predictions.csv`

This file contains crucial columns:
- `Amount`: Transaction amount
- `fraud_probability`: Probability from Gradient Boosting
- `fraud_risk`: The Hybrid Risk Score (0-1)
- `Class`: Actual Fraud Status (0 or 1)
- `UserID`: User Identifier

## 2. Import into Power BI
1. Open Power BI Desktop.
2. Click **Get Data** -> **Text/CSV**.
3. Select `outputs/fraud_predictions.csv`.
4. Click **Load**.

## 3. Create the Visuals
Use the drag-and-drop interface to build the following charts requested:

### A. Fraud Risk by Transaction
- **Visual**: Scatter Plot
- **X-Axis**: `Time` or `Index`
- **Y-Axis**: `fraud_risk`
- **Legend/Color**: `Class` (Red for Fraud, Blue for Normal)

### B. High-Risk Customers
- **Visual**: Table or Bar Chart
- **Rows**: `UserID`
- **Values**: Average of `fraud_risk` (Sort Descending)
- **Filter**: `fraud_risk` > 0.8

### C. Evaluation Metrics (Card Visuals)
- Create a measure for **Total Transactions**: `Count(Amount)`
- Create a measure for **Predicted Frauds**: Count where `fraud_risk > 0.5`
