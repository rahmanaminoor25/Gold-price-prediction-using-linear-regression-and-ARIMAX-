## Machine learning model for predicting the price of gold

The objective of this project is to create a machine learning model that accuratly predicts the price of gold. From looking at https://www.sbcgold.com/blog/10-factors-regularly-influence-gold-prices/, we chose these feature variables as a starting point:

1) Interest rates - To account for interest rates, we took data from 'Market yield on U.S. Treasury securities at 20-year  constant maturity' (i.e. it reflects the amount of interest you pay from a tresury bond issued today in twenty years time).
Data source: https://www.federalreserve.gov/datadownload/Output.aspx?rel=H15&series=bf17364827e38702b42a58cf8eaa3f78&lastobs=&from=&to=&filetype=csv&label=include&layout=seriescolumn&type=package

2) Inflation rates - 
Data source: https://fred.stlouisfed.org/graph/fredgraph.csv?bgcolor=%23ebf3fb&chart_type=line&drp=0&fo=open%20sans&graph_bgcolor=%23ffffff&height=450&mode=fred&recession_bars=on&txtcolor=%23444444&ts=12&tts=12&width=1140&nt=0&thu=0&trc=0&show_legend=yes&show_axis_titles=yes&show_tooltip=yes&id=T10YIE&scale=left&cosd=2016-01-27&coed=2026-01-23&line_color=%230073e6&link_values=false&line_style=solid&mark_type=none&mw=3&lw=3&ost=-99999&oet=99999&mma=0&fml=a&fq=Daily&fam=avg&fgst=lin&fgsnd=2020-02-01&line_index=1&transformation=lin&vintage_date=2026-01-27&revision_date=2026-01-27&nd=2003-01-02

3) Value of the dollar - US dollar index is taken to account. Data source: https://fred.stlouisfed.org/series/DTWEXBGS

4) S&P500 - A stock market index which tracks the top 500 leading publicly listed companies in America. In a sense tracks the economic performance of USA. Source for data: https://fred.stlouisfed.org/series/SP500

5) Past gold price - It goes without saying that the price of gold the day/ a week / three months before will be colinear with the current gold price. We expect this feature to be the strongest predictor for the future price. Data source: https://freegoldapi.com/


## Other features 

Upon further research, we decided to implement the following additional features:

- University of Michigan: Consumer Sentiment - Captures consumer sentiment. Historically, low confidence has correlated with higher gold prices (source: https://www.mcoscillator.com/learning_center/weekly_chart/gold_and_consumer_sentiment_extremes/). Data source: https://fred.stlouisfed.org/series/UMCSENT

- CBOE Gold ETF Volatility Index -  Aims at capturing the market sentiment and percieved risk of the market via the volatility of the SPDR Gold Shares ETF (GLD). Data source: https://fred.stlouisfed.org/series/GVZCLS

- CBOE Volatility Index: VIX - Captures the volitility of the S&P 500 and is often used by investors as it provides a quantifiable measure  investor fear and uncertainty. Data source: https://fred.stlouisfed.org/series/VIXCLS



## Model

We intend to use multiple linear regression to model the data. In order to track the price gold tommorow/ next week/ in the next three months, We simply take the current price of gold and shift it by 1/ 7/ 31 units. This then serves as the target variable. 

For each of the model type*, we create two models- one model uses the current gold price as a feature, the other model does not include this feature.

### Model 1

Model 1 aims at predicting the price of gold tommorow. Data is not normalised and ridge regression is not applied.

### Model 2

Model 2 aims at predicting the price of gold after one week. Data is not normalised and ridge regression is not applied.

### Model 3 

Model 3 aims at predicting the price of gold in one months time. Data is not normalised and ridge regression is not applied.

### Model 4 

Model 3 aims at predicting the price of gold in three months time. Data is not normalised and ridge regression is not applied.


### Model 5

Model 4 aims at predicting the price of gold in one months time. This model however, includes the additional features mentioned above, underneath 'Other features'. Data this time is normalised and ridge regression is applied.

We also then conduct tests to verify if the level of autocorrelation between current gold prices and future (lagged) prices.
