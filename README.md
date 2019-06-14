# CryptoCurrencyConversionProject
Project to Create Service in Java Spring to Get BTC Values in USD

Summary of the Application
----------------------
Application is developed with Java Spring Framework.
For the details how the architecture looks like, please refer to the diagram uploaded in the project.

Information Fetching has been scheduled and defined in config.properties. Periodically, the call from the Service is being done to get the information and store it into the database.

With Controller, the HTTP API has been exposed for third party to get information about last rate that has been fetched in database and list of the rates defined by the date period.

Configuration
-------------
Service regularly fetches 1BTC value in USD currency and storing it in database (Internal H2 database).
Time period to fetch the values is configurable and can be defined in config.properties.
**************************************
Current Setup of the config.properties
**************************************
exchangerate.interval=10000

Usage of the Service
--------------------
Service provides two HTTP API calls:
1) Get Latest Value that has been Stored in Database
To get the last Value, /LatestRate needs to be called
*******************
Example of the Call
*******************
Call: 
------
http://localhost:8080/LatestRate

Response:
--------
{"crytpoCurrency":"BTC","currency":"USD","conversionDate":"2019-06-13T21:16:59.117","rateValue":8218.74857,"id":422}

2) Get List of Values that have been Stored in Database based on the dates provided
To Get list of Values, /HistoricalRates needs to be called
*******************
Example of the Call
*******************
Call: 
------
http://localhost:8080/HistoricalRates?startDate=2019-06-13T21:10:43.503&endDate=2019-06-13T21:59:43.503

Response:
--------
[{"crytpoCurrency":"BTC","currency":"USD","conversionDate":"2019-06-13T21:24:41.914","rateValue":8244.8755,"id":258},{"crytpoCurrency":"BTC","currency":"USD","conversionDate":"2019-06-13T21:24:46.848","rateValue":8244.8755,"id":259},{"crytpoCurrency":"BTC","currency":"USD","conversionDate":"2019-06-13T21:24:52.817","rateValue":8244.8755,"id":260},{"crytpoCurrency":"BTC","currency":"USD","conversionDate":"2019-06-13T21:24:58.792","rateValue":8244.8755,"id":261},{"crytpoCurrency":"BTC","currency":"USD","conversionDate":"2019-06-13T21:25:04.75","rateValue":8244.8755,"id":262},{"crytpoCurrency":"BTC","currency":"USD","conversionDate":"2019-06-13T21:27:12.928","rateValue":8241.91698,"id":290},{"crytpoCurrency":"BTC","currency":"USD","conversionDate":"2019-06-13T21:27:17.719","rateValue":8241.91698,"id":291},{"crytpoCurrency":"BTC","currency":"USD","conversionDate":"2019-06-13T21:27:23.728","rateValue":8241.91698,"id":292},{"crytpoCurrency":"BTC","currency":"USD","conversionDate":"2019-06-13T21:27:29.777","rateValue":8241.91698,"id":293},{"crytpoCurrency":"BTC","currency":"USD","conversionDate":"2019-06-13T21:28:23.072","rateValue":8245.875,"id":322}]


