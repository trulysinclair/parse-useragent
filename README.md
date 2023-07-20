# Fast Middleware exposing user-agent for [NodeJS](http://nodejs.org/)

@trulysinclair/parse-useragent is a simple NodeJS/ExpressJS user-agent middleware exposing user-agent details to your application and views.

## Installation

```bash
# npm
npm install --save @trulysinclair/parse-useragent
# Yarn
yarn add @trulysinclair/parse-useragent
```

## Usage overview

### Simple Node App

```js
var http = require("http"),
  useragent = require("@trulysinclair/parse-useragent");

var app = http.createServer(function(req, res) {
  var source = req.headers["user-agent"],
    ua = useragent.parse(source);
  res.writeHead(200, { "Content-Type": "text/plain" });
  res.end(JSON.stringify(ua));
});

app.listen(3000);
```

<!-- #### manual setup in project config/middleware.js

```js
var useragent = require("@trulysinclair/parse-useragent");

module.exports = function(app, express) {
  app.use(function() {
    app.use(useragent.express());
  });
};
``` -->

### For [ExpressJS](http://expressjs.com/)

```js
var express = require("express");
var app = express();
var useragent = require("@trulysinclair/parse-useragent");

app.use(useragent.express());
app.get("/", function(req, res) {
  res.send(req.useragent);
});
app.listen(3000);
```

module provides details such as the following:

```js
{
  "isMobile":false,
  "isDesktop":true,
  "isBot":false,
  .....
  "browser":"Chrome",
  "version":"17.0.963.79",
  "os":"Windows 7",
  "platform":"Microsoft Windows",
  "source":"Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/535.11 (KHTML, like Gecko) Chrome/17.0.963.79..."
}
```

## Accessing the User-Agent

If you are using `express` or `connect`, then `@trulysinclair/parse-useragent`
provides an easy way to access the user-agent as:

- `req.useragent` from your app server
- `useragent` helper accessible from your `express` views.

<!-- ## Client Side

- Clone the repo: `git clone git://github.com/biggora/@trulysinclair/parse-useragent.git`
- Or Install with [Bower](http://twitter.github.com/bower): `bower install @trulysinclair/parse-useragent`.

The client side version of @trulysinclair/parse-useragent available in the `lib/` subdirectory.

#### Include file in your HTML. The minimum required for this plugin are:

```
<script type="text/javascript" src="/path/to/@trulysinclair/parse-useragent.js"></script>
```

#### Execute the plugin:

```javascript
var userAgent = new UserAgent().parse(navigator.userAgent);
``` -->

## Running Tests

Ensure you have [nodeunit](https://github.com/caolan/nodeunit) by running `npm install -g nodeunit`.
Then, run `npm test`.

```bash
npm install
npm test
```

### Run Example Node App

```bash
npm run-script http
```

### Run Example Express App

```bash
npm run-script express
```

## Original Author of `express-useragent`

Aleksejs Gordejevs <aleksej@gordejev.lv>

## License

(The MIT License)

Copyright (c) 2023 TrulySinclair <truly.sinclair@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
