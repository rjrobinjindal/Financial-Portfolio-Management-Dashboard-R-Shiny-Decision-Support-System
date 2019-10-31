# Financial-Portfolio-Management-Dashboard-R-Shiny-Decision-Support-System

Abstract
We have developed a shiny dashboard application that allows users to track the performance of S&P stocks, observe their forecast predictions and curate a stock portfolio based on the user’s financial goals and risk appetite. This application can be leveraged to support asset managers in portfolio management. We have designed the tool to perform a comprehensive analysis of stock data using descriptive, predictive and prescriptive analytics. We also implemented the ARIMA model for time series analysis.
Business Problem
For an Asset Manager who does not have the time and bandwidth to carry out sophisticated financial analysis, the portfolio management dashboard is a very effective tool. Since it is algorithm-driven, the dashboard also provides more accurate recommendations based on real-time data.
The portfolio management tool addresses the two key questions of a potential retail investor:
1. Which are the stocks that should I invest in?
2. How much should I invest in each of these stocks?
The dashboard generates a portfolio of stocks curated for four different profiles of investors:
1. The high-return investor: Maximize ROI
2. The risk-averse investor: Minimize risk
3. Diversified portfolio profile: Constraints (min-max) on stock options to maximize ROI
4. Balanced portfolio investor: Maximize sharpe1 ratio
On average, the optimizer tool would match the S&P annual return of ~10%2 whereas the average retail investor typically gets a return of 6% on his/her stock investments.
Analytics Problem
The business problem can be formulated into an optimization problem with the objective of maximizing the Return-Risk ratio, with different user-defined constraints (such as min expected return, number of stocks to be selected in the portfolio, max risk tolerance, etc.)
Maximize ([Return-(risk free return)/Risk] or [Max Returns] or [Minimum Risk] ) Subject to ([Overall returns] or [Minimum Weights] or [Maximum Weights])
The success of the solution lies in its ability to generate multiple portfolios which curated to the specific investor’s risk appetite and financial goals.
By their nature, stock markets are inherently unpredictable, the predictions come with the underlying assumption that returns will have an underlying risk (variance in return) associated with it.
Data
We narrowed down our focus to S&P stocks which are typically more attractive for the Asset Managers whose clients are retail investors. The stock data is imported from Yahoo Finance (starting from Jan 1st, 2013)
Since the data is already in a clean, structured, and standardized format, we did not apply additional data cleaning methods. We used financial functions to generate returns/get inherent risk (standard deviation) for every stock.
The data granularity is at a daily level – This data is used to generate the technical indicators
1 Sharpe Ratio: a measure that indicates the average return minus the risk-free return divided by the standard deviation of
return on an investment 2
 1
Methodology Selection
We designed the product to support the investor in each step of the decision process:
1. Explore (descriptive analytics): Identify the stocks and review their past performance. Filter down
the stocks that have good finance ratios/technical indicators.
2. Forecast (predictive analytics): Estimate the expected growth of a stock based on current trends.
This analysis is used to further filter the stocks for the portfolio.
3. Optimize (prescriptive analytics): An optimized portfolio curated to the investor’s specifications.
This allows the asset manager to split the funds optimally across individual financial assets.
Pre-existing libraries such as ‘quantmod’, ‘PortfolioAnalytics’, ‘dplyr’ make ‘R’ the most ideal tool to
develop this application. Moreover, Shiny with R served as an excellent visualization platform.
Model Building
To calibrate the model in time series, data checked for stationarity through the ADF3 test. ARIMA4, a widely used time series algorithm, was leveraged to deploy the “Forecast” module and to estimate the return from stocks. This estimated ROI data is fed into four different optimizer models that cater to the different profiles of investors.
As discussed in the “Business Problem” section, different models allocate weights based on specific objective functions and user-defined constraints. The objective functions in each of these models aim to either maximize Sharpe Ratio and/or maximize returns and/or minimize the risk in the portfolio.
The team has rigorously stress-tested these optimization models to account for fringe cases and launched a fully productionable version of the model after multiple iterations. This testing Is done by validating for optimization models by relaxing constraints.
Functionality and GUI Design
The dashboard has 3 separate windows serving each of the modules described above, viz., Explore, Forecast and Optimize. The Yeti theme and sidebar panel layout make the user interface in the dashboard neat, sleek and seamless. The interactive plots in the dashboard highlight information at different hierarchic levels.
Further functionalities that can be added to the app would be increased forecasting models to account for multiple regressors. Also highly advanced versions of optimizers can be deployed to obtain global optima in portfolio management.
Conclusions
The application generates a highly efficient balanced portfolio which helps asset manager manage the risks/get desired returns. The present application has a few limitations such as, narrow focus on financial asset selection, a quantitative bias in modeling, etc. The application can be further developed to optimize risks and returns more holistically.
3 Augmented Dickey-Fuller test tests the null hypothesis that a unit root is in a time series sample 4 Auto-Regressive Integrated Moving Average
 2

References
1. Shiny Reactive Tutorial (https://shiny.rstudio.com/tutorial/written-tutorial/lesson6/)
2. Shiny function reference (https://shiny.rstudio.com/reference/shiny/1.0.5/)
3. Quantmod library (https://www.quantmod.com/)
4. ARIMA Forecast (https://rdrr.io/cran/forecast/man/forecast.Arima.html)
5. Portfolio Analytics (https://cran.r- project.org/web/packages/PortfolioAnalytics/vignettes/portfolio_vignette.pdf)
6. Charting Portfolios (https://moderndata.plot.ly/portfolio-optimization-using-r-and-plotly/)
       
