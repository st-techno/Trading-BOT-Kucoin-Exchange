
# CHATGPT Crypto Trading Bot

## This is a trading script for KuCoin that continuously places buy and sell orders based on market data and a predictive model generated by OpenAI's GPT-3.5 language model.

### Requirements -- We use conda for enviroments and it is what the requirments.txt is made with.
ccxt
openai

### Setup
Install the required packages: pip install ccxt openai
Replace EXCHANGE_NAME with the name of the exchange you want to use.
Set sandbox mode to True or False by setting enabled to True or False.
Set your API keys by replacing the empty strings for apiKey, secret, and password.
Set the symbol you want to trade on KuCoin by replacing 'BTC/USDT' with your desired symbol.

### Setup your KuCoin API keys here https://www.kucoin.com/support/360015102174
Get your OpenAI keys https://platform.openai.com/account/api-keys

### How it works
This script is a trading algorithm for the KuCoin cryptocurrency exchange. It retrieves the current trading data for the specified symbol and window time frame, fetches the current ticker information for the symbol, and places buy or sell orders based on the midpoint price, which is the average of the current bid and ask prices. The script also uses the OpenAI API to ask a language model, represented here by ChatGPT, for a prediction on whether the market is going up or down before placing a buy order.

The first section of the script sets up the time frames that can be used in the algorithm and imports the necessary libraries, including the ccxt library for interacting with the KuCoin exchange and the OpenAI API library.

The next section of the script sets the exchange name to KuCoin and instantiates the exchange class using ccxt. The API keys are set next, along with the symbol to trade on KuCoin. The while loop is then started to begin the trading script.

Within the while loop, data is batch streamed from KuCoin using the fetch_ohlcv function with the symbol and window time frame. A nested while loop is started to allow for continuous trading. The current ticker information for the symbol is fetched using fetch_ticker, and the current bid and ask prices are checked. The midpoint price is calculated by averaging the bid and ask prices, and a premium is set for the sell order.

The balance for selling is retrieved using fetch_balance. The OpenAI API is used to ask ChatGPT whether the market is going up or down. If there are no open orders, a limit buy order is placed at the midpoint price. If there are open orders, the script waits for a few seconds and then checks the status of the open orders again. If there are still no open orders, the script places a limit sell order at the midpoint price plus the premium.

The script prints out the current market data and any errors that occur. It also prints out the ChatGPT response on whether the market is going up or down. The sleep function is used to pause the script for a few seconds before checking the status of the open orders again.

### How to use it in detail
To set up and use this script, you can follow these steps using Conda:

Install Anaconda or Miniconda, which are Python distribution platforms that make it easier to manage packages and dependencies.
Create a new Conda environment for this project by opening the Anaconda Prompt (Windows) or the terminal (MacOS/Linux) and running the following command:
```
conda create --name trading-bot python=3.8
```
This will create a new environment called "trading-bot" with Python 3.8 installed.

Activate the new environment by running:
```
conda activate trading-bot
```
Install the required packages using pip by running the following command:
```
pip install ccxt openai
```
This will install the CCXT and OpenAI Python libraries.

Open the script file in a text editor or IDE of your choice, and replace the placeholder values for the Kucoin API keys with your own.

Run the script by running the following command in the terminal:
```
python trading_bot.py
```
This will start the trading bot, which will continuously fetch market data, use OpenAI's GPT-3.5 model to predict market trends, and place buy and sell orders accordingly.

Note: Before running the bot with real money, it's recommended to test it with a demo account or in sandbox mode. You can enable sandbox mode by changing the value of enabled to True in the following line:

```
exchange.set_sandbox_mode(enabled=False)
to:


exchange.set_sandbox_mode(enabled=True)
```
This will allow you to test the bot without risking real funds.

### Time frame
You can select the desired time frame by choosing from the following options:
```
'1m': '1min'
'3m': '3min'
'5m': '5min'
'15m': '15min'
'30m': '30min'
'1h': '1hour'
'2h': '2hour'
'4h': '4hour'
'6h': '6hour'
'8h': '8hour'
'12h': '12hour'
'1d': '1day'
'1w': '1week'
```
