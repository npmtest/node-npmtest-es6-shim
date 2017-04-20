# npmtest-es6-shim

#### basic test coverage for  [es6-shim (v0.35.3)](https://github.com/paulmillr/es6-shim/)  [![npm package](https://img.shields.io/npm/v/npmtest-es6-shim.svg?style=flat-square)](https://www.npmjs.org/package/npmtest-es6-shim) [![travis-ci.org build-status](https://api.travis-ci.org/npmtest/node-npmtest-es6-shim.svg)](https://travis-ci.org/npmtest/node-npmtest-es6-shim)

#### ECMAScript 6 (Harmony) compatibility shims for legacy JavaScript engines

[![NPM](https://nodei.co/npm/es6-shim.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/es6-shim)

| git-branch : | [alpha](https://github.com/npmtest/node-npmtest-es6-shim/tree/alpha)|
|--:|:--|
| coverage : | [![istanbul-coverage](https://npmtest.github.io/node-npmtest-es6-shim/build/coverage.badge.svg)](https://npmtest.github.io/node-npmtest-es6-shim/build/coverage.html/index.html)|
| test-report : | [![test-report](https://npmtest.github.io/node-npmtest-es6-shim/build/test-report.badge.svg)](https://npmtest.github.io/node-npmtest-es6-shim/build/test-report.html)|
| build-artifacts : | [![build-artifacts](https://npmtest.github.io/node-npmtest-es6-shim/glyphicons_144_folder_open.png)](https://github.com/npmtest/node-npmtest-es6-shim/tree/gh-pages/build)|

- [https://npmtest.github.io/node-npmtest-es6-shim/build/coverage.html/index.html](https://npmtest.github.io/node-npmtest-es6-shim/build/coverage.html/index.html)

[![istanbul-coverage](https://npmtest.github.io/node-npmtest-es6-shim/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fcoverage.lib.html.png)](https://npmtest.github.io/node-npmtest-es6-shim/build/coverage.html/index.html)

- [https://npmtest.github.io/node-npmtest-es6-shim/build/test-report.html](https://npmtest.github.io/node-npmtest-es6-shim/build/test-report.html)

[![test-report](https://npmtest.github.io/node-npmtest-es6-shim/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Ftest-report.html.png)](https://npmtest.github.io/node-npmtest-es6-shim/build/test-report.html)

- [https://npmdoc.github.io/node-npmdoc-es6-shim/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-es6-shim/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-es6-shim/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-es6-shim/build/apidoc.html)

![npmPackageListing](https://npmtest.github.io/node-npmtest-es6-shim/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmtest.github.io/node-npmtest-es6-shim/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "name": "es6-shim",
    "version": "0.35.3",
    "author": "Paul Miller (http://paulmillr.com)",
    "description": "ECMAScript 6 (Harmony) compatibility shims for legacy JavaScript engines",
    "keywords": [
        "ecmascript",
        "harmony",
        "es6",
        "shim",
        "promise",
        "promises",
        "setPrototypeOf",
        "map",
        "set",
        "__proto__"
    ],
    "homepage": "https://github.com/paulmillr/es6-shim/",
    "license": "MIT",
    "repository": {
        "type": "git",
        "url": "git://github.com/paulmillr/es6-shim.git"
    },
    "main": "es6-shim",
    "scripts": {
        "pretest": "npm run --silent lint && evalmd *.md",
        "test": "npm run --silent tests-only",
        "tests-only": "npm run --silent test:shim && npm run --silent test:sham",
        "test:shim": "mocha test/*.js test/*/*.js",
        "test:sham": "mocha test-sham/*.js",
        "test:native": "NO_ES6_SHIM=1 npm run --silent tests-only",
        "lint": "npm run --silent lint:shim && npm run --silent lint:sham",
        "lint:shim": "npm run --silent jshint:shim && npm run --silent jscs:shim && npm run --silent eslint:shim",
        "lint:sham": "npm run --silent jshint:sham && npm run --silent jscs:sham && npm run --silent eslint:sham",
        "eslint": "npm run --silent eslint:shim && npm run --silent eslint:sham",
        "eslint:shim": "eslint es6-shim.js test/*.js test/*/*.js",
        "eslint:sham": "eslint es6-sham.js test-sham/*.js",
        "jshint": "npm run --silent jshint:shim && npm run --silent jshint:sham",
        "jshint:shim": "jshint es6-shim.js test/*.js test/*/*.js",
        "jshint:sham": "jshint es6-sham.js test-sham/*.js",
        "jscs": "npm run --silent jscs:shim && npm run --silent jscs:sham",
        "jscs:shim": "jscs es6-shim.js test/*.js test/*/*.js",
        "jscs:sham": "jscs es6-sham.js test-sham/*.js",
        "minify": "npm run --silent minify:shim && npm run --silent minify:sham",
        "minify:shim": "uglifyjs es6-shim.js --keep-fnames --comments --source-map=es6-shim.map -m -b ascii_only=true,beautify=false > es6-shim.min.js",
        "minify:sham": "uglifyjs es6-sham.js --keep-fnames --comments --source-map=es6-sham.map -m -b ascii_only=true,beautify=false > es6-sham.min.js",
        "sauce-connect": "curl -L https://gist.githubusercontent.com/henrikhodne/9322897/raw/sauce-connect.sh | bash && export TRAVIS_SAUCE_CONNECT=true",
        "sauce": "npm run --silent sauce-connect && grunt sauce"
    },
    "testling": {
        "html": "testling.html",
        "browsers": [
            "iexplore/6.0..latest",
            "firefox/3.0..6.0",
            "firefox/10.0",
            "firefox/15.0..latest",
            "firefox/nightly",
            "chrome/4.0..10.0",
            "chrome/20.0..latest",
            "chrome/canary",
            "opera/10.0..latest",
            "opera/next",
            "safari/4.0..latest",
            "ipad/6.0..latest",
            "iphone/6.0..latest",
            "android-browser/4.2..latest"
        ]
    },
    "dependencies": {},
    "devDependencies": {
        "chai": "^3.5.0",
        "es5-shim": "^4.5.9",
        "eslint": "^3.14.0",
        "@ljharb/eslint-config": "^10.0.0",
        "grunt": "^0.4.5",
        "grunt-contrib-connect": "^1.0.2",
        "grunt-contrib-watch": "^1.0.0",
        "grunt-saucelabs": "^8.6.3",
        "jscs": "^3.0.7",
        "jshint": "^2.9.4",
        "mocha": "^3.2.0",
        "promises-aplus-tests": "^2.1.2",
        "promises-es6-tests": "^0.5.0",
        "uglify-js": "2.7.3",
        "evalmd": "^0.0.17"
    }
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
