# OpenStack Passport

A simple token-based service for allocating OpenStack Public Cloud credit available to use at all participating vendors.

## Methods

### GET /tokens/:token

Returns 200 OK
```json
{
  "available_credit": {
    "unit": "cents",
    "currency": "usd",
    "amount": 10000
  }
}
```

or

Returns 404 Not Found
(no content)

### PUT /tokens/:token

Payload:
```json
{
  "unit": "cents",
  "currency": "usd",
  "amount": 10000
}
```

Returns 200 OK
```json
{
  "confirmation_token": "xyz321",
  "remaining_credit": {
    "unit": "cents",
    "currency": "usd",
    "amount": 0
  }
}
```

or

Returns 404 Not Found
(no content)

or

Returns 422 Unprocessable Entity
```json
{
  "error": "Insufficient credit. $10 remaining."
}
```
