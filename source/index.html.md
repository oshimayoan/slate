---
title: Vospay API Doc v0.1.5
language_tabs:
  - nodejs: JavaScript
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2
---

<h1 id="Vospay-API-Doc">Vospay API Doc v0.1.5</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Vospay API documentation using swagger 3.0.0

Base URLs:

* <a href="https://api-staging.vospay.id/api/v1">https://api-staging.vospay.id/api/v1</a>

# Authentication

* HTTP Authentication, scheme: bearer A generated JWT access token by `/authentication` endpoint

<h1 id="Vospay-API-Doc-Accounts">Accounts</h1>

## GET_accounts-accountID

<a id="opIdGET_accounts-accountID"></a>

> Code samples

```nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api-staging.vospay.id/api/v1/accounts/{accountID}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

`GET /accounts/{accountID}`

_Get full info detail about given account ID_

This endpoint is to get info from certain vospay account

<h3 id="GET_accounts-accountID-parameters">Parameters</h3>

| Parameter | In   | Type   | Required | Description           |
| --------- | ---- | ------ | -------- | --------------------- |
| accountID | path | string | true     | Vospay account number |

> Example responses

```json
{
  "id": "2340010000000001",
  "userID": "1234567890123456",
  "merchantLogo": "https://vospay.id/merchantLogo.png",
  "mfcLogo": "https://vospay.id/mfcLogo.png",
  "userFullName": "John Doe",
  "installments": [
    {
      "id": "1",
      "period": 3,
      "rate": 0.1
    },
    {
      "id": "2",
      "period": 6,
      "rate": 0.2
    },
    {
      "id": "3",
      "period": 9,
      "rate": 0.3
    },
    {
      "id": "4",
      "period": 12,
      "rate": 0.4
    }
  ]
}
```

```json
{
  "name": "string",
  "message": "string",
  "code": 0,
  "className": "string",
  "errors": {}
}
```

```json
{
  "name": "string",
  "message": "string",
  "code": 0,
  "className": "string",
  "errors": {}
}
```

<h3 id="GET_accounts-accountID-responses">Responses</h3>

| Status | Meaning                                                          | Description                                         | Schema |
| ------ | ---------------------------------------------------------------- | --------------------------------------------------- | ------ |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)          | OK response                                         | Inline |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1) | Response when vospay account number is not provided | Inline |
| 404    | [Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)   | Response when vospay account number is not found    | Inline |

<h3 id="GET_accounts-accountID-responseschema">Response Schema</h3>

Status Code **200**

| Name           | Type        | Required | Description                                                                    |
| -------------- | ----------- | -------- | ------------------------------------------------------------------------------ |
| » id           | string      | false    | Vospay account number                                                          |
| » userID       | string      | false    | User's KTP number / NIK (Country ID card) that linked to vospay account number |
| » merchantLogo | string(uri) | false    | Merchant logo URL                                                              |
| » mfcLogo      | string(uri) | false    | Multifinance company logo URL                                                  |
| » userFullName | string      | false    | Full Name of account's owner                                                   |
| » installments | [object]    | false    | Installment plans available for this account                                   |
| »» id          | string      | false    | Installment ID                                                                 |
| »» period      | number      | false    | Installment period (in month)                                                  |
| »» rate        | number      | false    | Installment rate                                                               |

Status Code **400**

| Name        | Type   | Required | Description    |
| ----------- | ------ | -------- | -------------- |
| » name      | string | false    | No description |
| » message   | string | false    | No description |
| » code      | number | false    | No description |
| » className | string | false    | No description |
| » errors    | object | false    | No description |

Status Code **404**

| Name        | Type   | Required | Description    |
| ----------- | ------ | -------- | -------------- |
| » name      | string | false    | No description |
| » message   | string | false    | No description |
| » code      | number | false    | No description |
| » className | string | false    | No description |
| » errors    | object | false    | No description |

<aside class="success">
This operation does not require authentication
</aside>

## GET_accounts

<a id="opIdGET_accounts"></a>

> Code samples

```nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api-staging.vospay.id/api/v1/accounts?phone=08118289855',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

`GET /accounts`

_Fetch all accounts using phone number_

This endpoint is for fetching all vospay accounts that certain phone number has. By default backend return list of existing accounts and send OTP if account isActived=true.

<h3 id="GET_accounts-parameters">Parameters</h3>

| Parameter | In    | Type   | Required | Description         |
| --------- | ----- | ------ | -------- | ------------------- |
| phone     | query | string | true     | User's phone number |

> Example responses

```json
{
  "vospayNumbers": [
    {
      "vospayNumber": "2340010000000001",
      "mfcLogo": "https://vospay.id/mfcLogo.png"
    },
    {
      "vospayNumber": "2340010000000002",
      "mfcLogo": "https://vospay.id/mfcLogo.png"
    },
    {
      "vospayNumber": "2340010000000003",
      "mfcLogo": "https://vospay.id/mfcLogo.png"
    },
    {
      "vospayNumber": "2340010000000004",
      "mfcLogo": "https://vospay.id/mfcLogo.png"
    }
  ]
}
```

```json
{
  "name": "string",
  "message": "string",
  "code": 0,
  "className": "string",
  "errors": {}
}
```

```json
{
  "name": "string",
  "message": "string",
  "code": 0,
  "className": "string",
  "data": {},
  "errors": {}
}
```

<h3 id="GET_accounts-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                             | Schema |
| ------ | -------------------------------------------------------------------------- | ------------------------------------------------------- | ------ |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | OK response                                             | Inline |
| 404    | [Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)             | Response when vospay account number is not found        | Inline |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Response when phone number is not provided or not found | Inline |

<h3 id="GET_accounts-responseschema">Response Schema</h3>

Status Code **200**

| Name            | Type        | Required | Description                                                |
| --------------- | ----------- | -------- | ---------------------------------------------------------- |
| » vospayNumbers | [object]    | false    | Array of vospay account numbers that one phone number had. |
| »» vospayNumber | string      | false    | Vospay account number                                      |
| »» mfcLogo      | string(uri) | false    | URL of multifinance logo                                   |

Status Code **404**

| Name        | Type   | Required | Description    |
| ----------- | ------ | -------- | -------------- |
| » name      | string | false    | No description |
| » message   | string | false    | No description |
| » code      | number | false    | No description |
| » className | string | false    | No description |
| » errors    | object | false    | No description |

Status Code **500**

| Name        | Type   | Required | Description    |
| ----------- | ------ | -------- | -------------- |
| » name      | string | false    | No description |
| » message   | string | false    | No description |
| » code      | number | false    | No description |
| » className | string | false    | No description |
| » data      | object | false    | No description |
| » errors    | object | false    | No description |

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="Vospay-API-Doc-Activation">Activation</h1>

## POST_activation

<a id="opIdPOST_activation"></a>

> Code samples

```nodejs
const request = require('node-fetch');
const inputBody = '{
  "mfcID": "234",
  "nik": "6308044810820001",
  "phone": "08118289855",
  "dateOfBirth": "1988-10-02"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api-staging.vospay.id/api/v1/activation',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

`POST /activation`

_Post user's data to generate and activate account number_

Use this endpoint when user submit their data on activation process

> Body parameter

```json
{
  "mfcID": "234",
  "nik": "6308044810820001",
  "phone": "08118289855",
  "dateOfBirth": "1988-10-02"
}
```

<h3 id="POST_activation-parameters">Parameters</h3>

| Parameter     | In   | Type   | Required | Description                                    |
| ------------- | ---- | ------ | -------- | ---------------------------------------------- |
| body          | body | object | true     | No description                                 |
| » mfcID       | body | string | true     | MFC's ID that sent the activation link to user |
| » nik         | body | string | true     | User's KTP number / NIK (Country ID card)      |
| » phone       | body | string | true     | User's phone number                            |
| » dateOfBirth | body | string | true     | User's date of birth                           |

> Example responses

```json
{
  "vospayNumber": "2340010000000002"
}
```

```json
{
  "name": "string",
  "message": "string",
  "code": 0,
  "className": "string",
  "errors": {}
}
```

<h3 id="POST_activation-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                                                                           | Schema |
| ------ | -------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ------ |
| 201    | [Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)               | OK response                                                                                           | Inline |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Response when Content-Type is not provided on request header or required request body is not provided | Inline |

<h3 id="POST_activation-responseschema">Response Schema</h3>

Status Code **201**

| Name           | Type   | Required | Description                          |
| -------------- | ------ | -------- | ------------------------------------ |
| » vospayNumber | string | false    | Auto generated vospay account number |

Status Code **500**

| Name        | Type   | Required | Description    |
| ----------- | ------ | -------- | -------------- |
| » name      | string | false    | No description |
| » message   | string | false    | No description |
| » code      | number | false    | No description |
| » className | string | false    | No description |
| » errors    | object | false    | No description |

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="Vospay-API-Doc-Authentication">Authentication</h1>

## POST_authentication

<a id="opIdPOST_authentication"></a>

> Code samples

```nodejs
const request = require('node-fetch');
const inputBody = '{
  "strategy": "otp",
  "phone": "08118289855",
  "otp": "7034"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api-staging.vospay.id/api/v1/authentication',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

`POST /authentication`

_Create access token to access some protected endpoints_

Use this endpoint for every otp

> Body parameter

```json
{
  "strategy": "otp",
  "phone": "08118289855",
  "otp": "7034"
}
```

<h3 id="POST_authentication-parameters">Parameters</h3>

| Parameter  | In   | Type   | Required | Description    |
| ---------- | ---- | ------ | -------- | -------------- |
| body       | body | object | true     | No description |
| » strategy | body | string | true     | No description |
| » phone    | body | string | true     | No description |
| » otp      | body | string | true     | No description |

> Example responses

```json
{
  "accessToken":
    "j91usej1ju983s1uen93du9e.ue9s831ue8913_EXAMPLE_uj38esu983eu98r.jf92ur982j3u8922932su392nc9j2e9"
}
```

```json
{
  "name": "string",
  "message": "string",
  "code": 0,
  "className": "string",
  "data": {
    "message": "string"
  },
  "errors": {}
}
```

<h3 id="POST_authentication-responses">Responses</h3>

| Status | Meaning                                                          | Description                                       | Schema |
| ------ | ---------------------------------------------------------------- | ------------------------------------------------- | ------ |
| 201    | [Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)     | OK response                                       | Inline |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1) | Response when phone number or otp is not provided | Inline |

<h3 id="POST_authentication-responseschema">Response Schema</h3>

Status Code **201**

| Name          | Type   | Required | Description                                                            |
| ------------- | ------ | -------- | ---------------------------------------------------------------------- |
| » accessToken | string | true     | A JWT access token generated by the server to authenticate user action |

Status Code **400**

| Name        | Type   | Required | Description    |
| ----------- | ------ | -------- | -------------- |
| » name      | string | false    | No description |
| » message   | string | false    | No description |
| » code      | number | false    | No description |
| » className | string | false    | No description |
| » data      | object | false    | No description |
| »» message  | string | false    | No description |
| » errors    | object | false    | No description |

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="Vospay-API-Doc-Transaction">Transaction</h1>

## POST_checkout

<a id="opIdPOST_checkout"></a>

> Code samples

```nodejs
const request = require('node-fetch');
const inputBody = '{
  "accountID": "2340010000000001",
  "merchantID": 1,
  "orderID": "B0001",
  "items": [
    {
      "id": "P0001",
      "description": "2 Product A",
      "cost": 10000
    },
    {
      "id": "P0002",
      "description": "1 Product B",
      "cost": 25000
    }
  ],
  "shippingCost": 5000,
  "insuranceCost": 1000,
  "processingFee": 2500,
  "tax": 0,
  "status": "Pending",
  "installmentID": 1
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'<<accessToken>>'

};

fetch('https://api-staging.vospay.id/api/v1/checkout',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

`POST /checkout`

_Post transaction data_

Use this endpoint to send transaction detail on submit a checkout

> Body parameter

```json
{
  "accountID": "2340010000000001",
  "merchantID": 1,
  "orderID": "B0001",
  "items": [
    {
      "id": "P0001",
      "description": "2 Product A",
      "cost": 10000
    },
    {
      "id": "P0002",
      "description": "1 Product B",
      "cost": 25000
    }
  ],
  "shippingCost": 5000,
  "insuranceCost": 1000,
  "processingFee": 2500,
  "tax": 0,
  "status": "Pending",
  "installmentID": 1
}
```

<h3 id="POST_checkout-parameters">Parameters</h3>

| Parameter       | In     | Type     | Required | Description                                                |
| --------------- | ------ | -------- | -------- | ---------------------------------------------------------- |
| Authorization   | header | string   | true     | A generated JWT access token by `/authentication` endpoint |
| body            | body   | object   | true     | No description                                             |
| » accountID     | body   | string   | true     | Vospay account number that used for transaction            |
| » merchantID    | body   | string   | true     | Merchant ID where transaction happens                      |
| » orderID       | body   | string   | true     | Order ID from the merchant                                 |
| » items         | body   | [object] | false    | List of purchased items                                    |
| »» id           | body   | string   | false    | ID of purchased item                                       |
| »» description  | body   | string   | false    | Name and amount of purchased item                          |
| »» cost         | body   | number   | false    | Total price of purchased item                              |
| » shippingCost  | body   | number   | false    | Shipping cost from transaction                             |
| » insuranceCost | body   | number   | false    | Insurance cost from transaction                            |
| » processingFee | body   | number   | false    | Additional fees from transaction (if there is)             |
| » tax           | body   | number   | false    | Tax or custom fee (e.g bea cukai) (if there is)            |
| » status        | body   | string   | false    | Status to tell backend about the transaction               |
| » installmentID | body   | string   | false    | ID of selected installment plan for the transaction        |

#### Enumerated Values

| Parameter | Value          |
| --------- | -------------- |
| » status  | Pending        |
| » status  | Approved       |
| » status  | Fulfilled      |
| » status  | Edit/Cancelled |
| » status  | Settled        |
| » status  | Refunded       |

> Example responses

```json
{
  "message": "Success"
}
```

```json
{
  "name": "string",
  "message": "string",
  "code": 0,
  "className": "string",
  "data": {},
  "errors": {}
}
```

```json
{
  "name": "string",
  "message": "string",
  "code": 0,
  "className": "string",
  "data": {},
  "errors": {}
}
```

<h3 id="POST_checkout-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                                                                        | Schema |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | ------ |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | OK response                                                                                        | Inline |
| 401    | [Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)            | Response when access token is not provided as Authorization on request header                      | Inline |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Response when Content-Type is not provided on request header or required request body not provided | Inline |

<h3 id="POST_checkout-responseschema">Response Schema</h3>

Status Code **200**

| Name      | Type   | Required | Description    |
| --------- | ------ | -------- | -------------- |
| » message | string | false    | No description |

Status Code **401**

| Name        | Type   | Required | Description    |
| ----------- | ------ | -------- | -------------- |
| » name      | string | false    | No description |
| » message   | string | false    | No description |
| » code      | number | false    | No description |
| » className | string | false    | No description |
| » data      | object | false    | No description |
| » errors    | object | false    | No description |

Status Code **500**

| Name        | Type   | Required | Description    |
| ----------- | ------ | -------- | -------------- |
| » name      | string | false    | No description |
| » message   | string | false    | No description |
| » code      | number | false    | No description |
| » className | string | false    | No description |
| » data      | object | false    | No description |
| » errors    | object | false    | No description |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
accessToken
</aside>

## POST_verify-transaction

<a id="opIdPOST_verify-transaction"></a>

> Code samples

```nodejs
const request = require('node-fetch');
const inputBody = '{
  "transactionID": "12ux0912examplej309128js01",
  "orderID": "01441-EXAMPLE-7615",
  "currency": "IDR",
  "grossAmount": 49500
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api-staging.vospay.id/api/v1/verify-transaction',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

`POST /verify-transaction`

_Verify transaction ID and order details_

Use this endpoint verify the transaction ID and order details with VOSPAY to ensure the integrity of the result received by the JavaScript callback

> Body parameter

```json
{
  "transactionID": "12ux0912examplej309128js01",
  "orderID": "01441-EXAMPLE-7615",
  "currency": "IDR",
  "grossAmount": 49500
}
```

<h3 id="POST_verify-transaction-parameters">Parameters</h3>

| Parameter       | In   | Type   | Required | Description                                       |
| --------------- | ---- | ------ | -------- | ------------------------------------------------- |
| body            | body | object | true     | No description                                    |
| » transactionID | body | string | true     | This is obtained from the TransactionResult       |
| » orderID       | body | string | true     | A unique (per merchant) identifier for this order |
| » currency      | body | string | true     | Used currency for the transaction                 |
| » grossAmount   | body | number | true     | The total amount of the order                     |

> Example responses

```json
{
  "status": "Valid"
}
```

```json
{
  "name": "string",
  "message": "string",
  "code": 0,
  "className": "string",
  "errors": {}
}
```

<h3 id="POST_verify-transaction-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                                                                           | Schema |
| ------ | -------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ------ |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | OK response                                                                                           | Inline |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Response when Content-Type is not provided on request header or required request body is not provided | Inline |

<h3 id="POST_verify-transaction-responseschema">Response Schema</h3>

Status Code **200**

| Name     | Type   | Required | Description               |
| -------- | ------ | -------- | ------------------------- |
| » status | string | false    | Status of the transaction |

Status Code **500**

| Name        | Type   | Required | Description    |
| ----------- | ------ | -------- | -------------- |
| » name      | string | false    | No description |
| » message   | string | false    | No description |
| » code      | number | false    | No description |
| » className | string | false    | No description |
| » errors    | object | false    | No description |

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="Vospay-API-Doc-Otp">Otp</h1>

## GET_otp-phoneNumber

<a id="opIdGET_otp-phoneNumber"></a>

> Code samples

```nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api-staging.vospay.id/api/v1/otp/{phoneNumber}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

`GET /otp/{phoneNumber}`

_Trigger backend to resend otp_

Use this endpoint to trigger the backend for resend the otp to a user

<h3 id="GET_otp-phoneNumber-parameters">Parameters</h3>

| Parameter   | In   | Type   | Required | Description         |
| ----------- | ---- | ------ | -------- | ------------------- |
| phoneNumber | path | string | true     | User's phone number |

> Example responses

```json
{
  "message": "Success"
}
```

```json
{
  "name": "string",
  "message": "string",
  "code": 0,
  "className": "string",
  "data": {},
  "errors": {}
}
```

<h3 id="GET_otp-phoneNumber-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                        | Schema |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------------- | ------ |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Backend successfuly resend the otp                 | Inline |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Response when phone number is not found or invalid | Inline |

<h3 id="GET_otp-phoneNumber-responseschema">Response Schema</h3>

Status Code **200**

| Name      | Type   | Required | Description    |
| --------- | ------ | -------- | -------------- |
| » message | string | false    | No description |

Status Code **500**

| Name        | Type   | Required | Description    |
| ----------- | ------ | -------- | -------------- |
| » name      | string | false    | No description |
| » message   | string | false    | No description |
| » code      | number | false    | No description |
| » className | string | false    | No description |
| » data      | object | false    | No description |
| » errors    | object | false    | No description |

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="Vospay-API-Doc-Registration">Registration</h1>

## POST_registration-accountID

<a id="opIdPOST_registration-accountID"></a>

> Code samples

```nodejs
const request = require('node-fetch');
const inputBody = '{
  "accountID": "2340010000000002",
  "email": "john@doe.com",
  "password": "abcd1234"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'<<accessToken>>'

};

fetch('https://api-staging.vospay.id/api/v1/registration',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

`POST /registration`

_Post user's registration data_

Use this endpoint to send registrant data when register submit is clicked

> Body parameter

```json
{
  "accountID": "2340010000000002",
  "email": "john@doe.com",
  "password": "abcd1234"
}
```

<h3 id="POST_registration-accountID-parameters">Parameters</h3>

| Parameter     | In     | Type   | Required | Description                                                |
| ------------- | ------ | ------ | -------- | ---------------------------------------------------------- |
| Authorization | header | string | true     | A generated JWT access token by `/authentication` endpoint |
| body          | body   | any    | true     | No description                                             |

> Example responses

```json
{
  "message": "Success"
}
```

```json
{
  "name": "string",
  "message": "string",
  "code": 0,
  "className": "string",
  "errors": {}
}
```

<h3 id="POST_registration-accountID-responses">Responses</h3>

| Status | Meaning                                                        | Description                                                      | Schema |
| ------ | -------------------------------------------------------------- | ---------------------------------------------------------------- | ------ |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)        | Backend successfuly store registrant data to database            | Inline |
| 404    | [Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4) | Response when vospay account number is not provided or not found | Inline |

<h3 id="POST_registration-accountID-responseschema">Response Schema</h3>

Status Code **200**

| Name      | Type   | Required | Description    |
| --------- | ------ | -------- | -------------- |
| » message | string | false    | No description |

Status Code **404**

| Name        | Type   | Required | Description    |
| ----------- | ------ | -------- | -------------- |
| » name      | string | false    | No description |
| » message   | string | false    | No description |
| » code      | number | false    | No description |
| » className | string | false    | No description |
| » errors    | object | false    | No description |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
accessToken
</aside>

# Schemas

<h2 id="tocSregister">Register</h2>

<a id="schemaregister"></a>

```json
{
  "accountID": "2340010000000002",
  "email": "john@doe.com",
  "password": "abcd1234"
}
```

### Properties

| Name      | Type          | Required | Description                      |
| --------- | ------------- | -------- | -------------------------------- |
| accountID | string        | true     | Registrant vospay account number |
| email     | string(email) | false    | Registrant email                 |
| password  | string        | true     | Registrant access code           |

<h2 id="tocSregisterfb">RegisterFB</h2>

<a id="schemaregisterfb"></a>

```json
{
  "accountID": "2340010000000002",
  "facebookAccount": "john@fb.com"
}
```

### Properties

| Name            | Type   | Required | Description                                                               |
| --------------- | ------ | -------- | ------------------------------------------------------------------------- |
| accountID       | string | true     | Registrant vospay account number                                          |
| facebookAccount | string | true     | Registrant facebook email if registrant registering with facebook account |
