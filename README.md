# Challenge


### Create an APP that gets and displays information from RockSpoon's Search API

- The app will have two screens:
  - The first one allows the user to search for items (plates) using RockSpoon Search API. The search can be performed using the search text field. 
  - The second screen displays information when an item is selected from the list.


- The hide option will remove that entry from the list. Ideally this should be persistent across multiple searches. In other words, if the user decides to hide on item it won't appear anymore. 
- Please consider the mockup below as a guide on how the page should be created.


![Mobile.png](https://github.com/supdevstar/cart-mobile-template/blob/main/Mobile.png)

### **The APP must have** ###

* __List of items page__: You can get it using the following call, replacing "burger" by the search term provided by the user (check [Swagger file](https://github.com/supdevstar/cart-mobile-template/blob/main/search-swagger.yaml)) :

```sh
curl --location --request POST 'https://stg-api.rockspoon.io/search/v2/composed' \
--header 'key: 56e379ffa58d2ac1a854abd75b2d76e5fa4b54e551332c83d7c87b3c2fd3caeada916dc330bab3cde7e72114874666cb6e94bd5c6e2b54fd1fbb41a99a9b85d7a3be2e2b1f8e5ba7ed75fbd170d0efaefe61d9b851815771d55048a53ebe34e0' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--data-raw '{ 
    "entity": "item",
    "page": 1,
    "size": 10,
    "params": {
        "term":["burger"]
    }
}'
```

* The page must get and display paginated results, with endless/infinite scroll (incrementing the `page` parameter).
* For each item, the App must show: Item's name, description, picture, and number of spoons.
* When selecting an item, the item details page must be displayed.
   
  
- __Item details page__. You can get it using the following call replacing {itemId} by the id of the item returned on the search (check [Swagger file](https://github.com/supdevstar/cart-mobile-template/blob/main/catalog-swagger.yaml)) : 
```sh
curl 'https://stg-api.rockspoon.io/catalog/consumer/item/{itemId}' \
  -H 'Accept: application/json' \
  -H 'key: 56e379ffa58d2ac1a854abd75b2d76e5fa4b54e551332c83d7c87b3c2fd3caeada916dc330bab3cde7e72114874666cb6e94bd5c6e2b54fd1fbb41a99a9b85d7a3be2e2b1f8e5ba7ed75fbd170d0efaefe61d9b851815771d55048a53ebe34e0'
```
  * The item's page must show: Item's name, tags, price, availableFor, and sizes and prices.


### MUST have
* Use a build system (Gradle for Android, Fastlane for iOS)
* JSON -> Object mapping (GSON / Jackson / Moshi / etc for Android, Codable for Swift)
* Material Design (Android only)

### Nice to have
* Framework for API communication (Moya + RxMoya on Swift)
* Unit tests or screen tests
* Functional tests (that browse the app as a use case)
* API and image caching
* Support orientation change without losing state

### Submission process

You must implement the code and send a pull request to the repository. 
