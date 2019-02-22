# Turing Front-end


## Welcome
Welcome to the Turing Challenge! We've provided some examples to guide you through the project.

## Root Endpoint 
[https://backendapi.turing.com/docs](https://backendapi.turing.com/docs)

## Authentication
Some endpoints require authentication. For more information, see the documentation. 

Token Example: ```Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjdXN0b21lcl9pZCI6MTIsIm5hbWUiOiJFZGVyIFRhdmVpcmEiLCJyb2xlIjoiY3VzdG9tZXIiLCJpYXQiOjE1NTA3ODYyMjAsImV4cCI6MTU1MDg3MjYyMH0.QEGdry367EQNxBqzuUDCGJscWkq8YQwJdGBgV3hztR0```
 
The token must be in the header param **user-key**. See example below.

Login Authentication Example (jQuery):
```javascript
$.ajax({ 
         url: "https://backendapi.turing.com/customer/login",
         data: {email: "CUSTOMER EMAIL", passsword: "CUSTOMER PASSWORD"},
         type: "POST",
         success: function(resp) { console.log(resp.responseText); },
         error: function(error) { console.log(error.responseText); }
});		
```

Response Example:
```json
{
  "user": {
    "customer_id": 12,
    "name": "Eder Taveira",
    "email": "challenge@turing.com",
    "address_1": "",
    "address_2": "",
    "city": "",
    "region": "",
    "postal_code": "",
    "shipping_region_id": null,
    "day_phone": null,
    "eve_phone": null,
    "mob_phone": null
  },
  "accessToken": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjdXN0b21lcl9pZCI6MTIsIm5hbWUiOiJFZGVyIFRhdmVpcmEiLCJyb2xlIjoiY3VzdG9tZXIiLCJpYXQiOjE1NTA3ODYyMjAsImV4cCI6MTU1MDg3MjYyMH0.QEGdry367EQNxBqzuUDCGJscWkq8YQwJdGBgV3hztR0",
  "expires_in": "24h"
}
```

Header & Token Example:
```javascript
$.ajax({ 
         url: "https://backendapi.turing.com/customer",
         headers: { 'user-key': 'Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjdXN0b21lcl9pZCI6MTIsIm5hbWUiOiJFZGVyIFRhdmVpcmEiLCJyb2xlIjoiY3VzdG9tZXIiLCJpYXQiOjE1NTA3ODYyMjAsImV4cCI6MTU1MDg3MjYyMH0.QEGdry367EQNxBqzuUDCGJscWkq8YQwJdGBgV3hztR0' },
         type: "GET",
         success: function(resp) { console.log(resp.responseText); },
         error: function(error) { console.log(error.responseText); }
});		
```

## Pagination
Pagination Params:

* **page** - Number of pages (Default is 1).
* **limit** - Limit for pages (Visit [the documentation](https://backendapi.turing.com/docs) for more information).

Examples: 

* https://backendapi.turing.com/categories?page=1&limit=20
* https://backendapi.turing.com/products?page=1
* https://backendapi.turing.com/products?limit=30

Note: Some endpoints such as shoppingcart and products do not require the param **description_length**.

Output Format:
```json
{
  "count": 40,
  "rows": [
    {
      "category_id": 1,
      "name": "French",
      "description": "The French have always had an eye for beauty. One look at the T-shirts below and you'll see that same appreciation has been applied abundantly to their postage stamps. Below are some of our most beautiful and colorful T-shirts, so browse away! And don't forget to go all the way to the bottom - you don't want to miss any of them!",
      "department_id": 1
    }
  ]
}
```

## Order

To sort a list, use the param **order**.

Param in REGEX is as follows: '/^([^\s]+),(DESC|ASC)$/'

Example: 

* https://backendapi.turing.com/categories?order=name|DESC
 


## Errors

Some error responses:

* **code** - Error's Code.
* **message** - Error's Message.
* **field** - Error's Field.

Error Example:
```json
{"error":{"status":400,"code":"USR_05","message":"The email don't exists.","field":"email"}}
```

