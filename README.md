# Customer Segmentation & Customer Value Analysis

RFM-based customer segmentation and revenue analysis using the Online Retail II dataset.

## Business Problem

Which customer segments are most valuable, and where should retention efforts be prioritized?

The goal of this analysis is to identify customer groups based on purchasing behavior and determine where retention and win-back efforts could have the greatest business impact.

## Dataset

The analysis uses the **Online Retail II** dataset, containing transaction-level data from a UK-based online retailer covering December 2009 to December 2011.

The dataset contains information such as:

- Invoice number
- Product
- Quantity
- Invoice date
- Unit price
- Customer ID
- Country

Monetary values are reported in **GBP (£)**.

The raw dataset is not included in this repository because of its size. See the **How to Run** section for instructions on where to place the dataset locally.

## Analysis Approach

The project follows these main steps:

### 1. Data Cleaning

- Investigate missing Customer IDs
- Identify and exclude cancellation transactions
- Investigate extreme quantities and invalid prices
- Remove duplicate records
- Exclude non-positive quantities and prices

### 2. RFM Analysis

Calculate three customer-level metrics:

- **Recency** — how recently the customer made a purchase
- **Frequency** — number of unique orders
- **Monetary** — total revenue generated

Each metric is converted into a 1–5 score, with higher scores representing stronger customer behavior.

### 3. Customer Segmentation

Customers are classified into behavioral segments including:

- Champions
- Loyal Customers
- New Customers
- Potential Loyalists
- At Risk
- Needs Attention
- Lost

### 4. Customer Value Analysis

The project analyzes:

- Historical customer revenue
- Average order value
- Observed monthly purchasing frequency
- Annualized revenue run-rate based on observed purchasing behavior

The annualized revenue run-rate is a descriptive projection and is **not a predictive Customer Lifetime Value (CLV) model**.

### 5. Business Recommendations

The analysis compares customer segments by:

- Customer count
- Revenue contribution
- Historical purchasing intensity
- Annualized revenue run-rate

These results are used to identify retention and win-back priorities.

## Key Findings

### Champions generate a disproportionate share of revenue

Champions represent approximately **25% of customers but generate around 69% of total revenue**.

This indicates a strong concentration of business value within a relatively small customer group.

**Recommendation:** protect Champions through loyalty initiatives, personalized engagement, and cross-sell/upsell opportunities.

### Customer count does not necessarily indicate business value

Lost customers form one of the largest customer groups, but contribute only around **4% of total revenue**.

This demonstrates why retention resources should be allocated based on customer value and behavior rather than segment size alone.

### At Risk customers are a stronger win-back opportunity than Lost customers

At Risk customers show a substantially higher historical annualized revenue run-rate than Lost customers.

This suggests that customers who are becoming inactive may still represent meaningful historical value and could justify more targeted win-back efforts.

**Recommendation:** prioritize personalized retention and win-back activity for **At Risk** customers, while using lower-cost re-engagement approaches for **Lost** customers.

## Important Limitation

The annualized revenue run-rate used in this project is a **descriptive projection based on observed purchasing behavior**.

It does not account for:

- Future churn probability
- Retention probability
- Profit margins
- Discounting
- Future changes in purchasing behavior

A predictive CLV model could be developed as a future extension.

## Potential Extensions

- Build a predictive CLV model using BG/NBD and Gamma-Gamma
- Perform cohort retention analysis
- Test win-back strategies using A/B testing
- Analyze customer behavior by product category
- Analyze customer segments by country

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Project Structure

```text
customer-segmentation-analysis/
│
├── README.md
├── customer_segmentation_clv.ipynb
└── .gitignore
```

The dataset is stored locally in a `data/` directory and is excluded from Git through `.gitignore`.

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/customer-segmentation-analysis.git
cd customer-segmentation-analysis
```

### 2. Download the Online Retail II dataset

Download the dataset separately and place the Excel file at:

```text
data/online_retail_II.xlsx
```

The `data/` directory can be created locally if it does not already exist.

### 3. Open the notebook

Open:

```text
customer_segmentation_clv.ipynb
```

using Jupyter Notebook, JupyterLab, or VS Code.

### 4. Run the notebook

Run the notebook from top to bottom.

The notebook will:

- Load the raw transaction data
- Clean the dataset
- Create customer-level RFM metrics
- Assign customer segments
- Calculate customer value metrics
- Generate visualizations and business insights

The raw Excel dataset and generated `.pkl` file are excluded from the repository through `.gitignore`.