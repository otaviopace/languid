# languid

A simple web framework, made for REST/JSON APIs

## Installation

`npm install --save languid`

## Usage
```javascript
const languid = require('languid')
const Promise = require('bluebird')

languid(req => {
  console.log(req.headers)
  console.log(req.body)
  return Promise.resolve({
    statusCode: 200,
    headers: {
      stuff:'content',
    },
    body: {
      ok: 'ok',
    },
  })
    .then(s => {
      throw new Error('stuff')
    })
    .catch(err => {
      // this will be the last response
      return {
        statusCode: 401,
        headers: {
          stuff:'bad content',
        },
        body: {
          bad: 'bad',
        },

      }
    })
})
  .listen(8000)
```
