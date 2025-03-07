# Asset Allocation guide for the Indian Market
The repsoitory contains asset_allocation.ipynb which is a data exploratory exercise to understand the performance of different asset classes available to the Indian investor.
It also contains momentum_based_random_forest_predictor.ipynb which is a random forest model to predict large drawdowns in the NIFTY 50.

Asset Allocation and Factor-based Systematic Equities Model for Indian Retail Investors
This document lays out all ideas that will drive the asset allocation for our systematic equities model. The primary objective of the rules defined in the document is to adjust allocation to Indian markets, foreign markets, and gold. It focuses only on those asset classes that are readily available for retails investors in India. 
Asset Classes:
1)	NIFTY 50 – Indian Equities
2)	S&P 500 – US Equities
3)	Hang Seng – Hong Kong (China) Equities
4)	Gold
5)	Debt – GILT Funds
What we need to do effectively is to come up with expected INR returns for each of these asset classes. Based on the expected returns we can create a portfolio with optimal allocation to each market.
Our investment strategy follows these steps:
1)	Calculate expected returns for the Indian market and adjust allocation to Indian market accordingly. The allocation range would be constrained between 0 to 100%
2)	We only diversify out of the Indian market if the negative outlook breaches a certain threshold – therefore, our strategy is returns are primarily driven by Indian equities – and diversification out of them is only used when outlook for Indian equities looks grim.
Calculating Expected Returns for Indian Equities:
We use the following predictor variables to predict market returns for Indian equities
1)	CAPE
2)	Dollar/INR exchange rate
3)	Momentum
A random forest model is training which uses different features based on CAPE, Dollar/INR Exchange Rate, and Momentum. It uses monthly data to predict drawdowns for the next month. Drawdown is defined as fall of more than 2% in the NIFTY 50.
If there is no drawdown prediction, we allocate 100% to our portfolio of 20 stocks as defined by the quantitative fundamental approach of stock selection.
If a drawdown is predicted, we allocate to a portfolio of gold, debt, and foreign equities. This portfolio is defined as follows:

Asset		Holding (%)
Gold		33.34
GILT Fund (ETF)		33.33
Foreign Equities	33.33
Total		100%


