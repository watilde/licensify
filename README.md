licensify
================================

Browserify plugin to prepend license header to your bundle

[![Build Status][travis-image]][travis-url]
[![NPM version][npm-image]][npm-url]
[![Dependency Status][depstat-image]][depstat-url]
[![License][license-image]][license-url]


DESCRIPTION
---------------------------------------

`licensify` is a browserify plugin to prepend license header to your bundle as follows.

```javascript
/**
 * Modules in this bundle
 * 
 * base64-js:
 *   license: MIT
 *   author: T. Jameson Little <t.jameson.little@gmail.com>
 *   maintainers: beatgammit <t.jameson.little@gmail.com>, feross <feross@feross.org>
 *   version: 0.0.8
 * 
 * buffer:
 *   license: MIT
 *   author: Feross Aboukhadijeh <feross@feross.org>
 *   maintainers: feross <feross@feross.org>
 *   contributors: Romain Beauxis <toots@rastageeks.org>, James Halliday <mail@substack.net>
 *   version: 3.3.1
 * 
 * core-util-is:
 *   license: MIT
 *   author: Isaac Z. Schlueter <i@izs.me>
 *   version: 1.0.1
 * 
 * events:
 *   author: Irakli Gozalishvili <rfobic@gmail.com>
 *   maintainers: gozala <rfobic@gmail.com>, shtylman <shtylman@gmail.com>
 *   version: 1.0.2
 * 
 * ieee754:
 *   license: MIT
 *   author: Feross Aboukhadijeh <feross@feross.org>
 *   maintainers: feross <feross@feross.org>
 *   contributors: Romain Beauxis <toots@rastageeks.org>
 *   version: 1.1.6
 * 
 * inherits:
 *   license: ISC
 *   version: 2.0.1
 * 
 * is-array:
 *   license: MIT
 *   maintainers: retrofox <rdsuarez@gmail.com>
 *   version: 1.0.1
 * 
 * isarray:
 *   license: MIT
 *   author: Julian Gruber <mail@juliangruber.com>
 *   maintainers: juliangruber <julian@juliangruber.com>
 *   version: 0.0.1
 * 
 * licensify:
 *   license: MIT
 *   author: Takuto Wada <takuto.wada@gmail.com>
 *   contributors: Okuno Kentaro, Ayumu Sato
 *   version: 1.1.0
 * 
 * process:
 *   author: Roman Shtylman <shtylman@gmail.com>
 *   maintainers: coolaj86 <coolaj86@gmail.com>, defunctzombie <shtylman@gmail.com>
 *   version: 0.11.1
 * 
 * process-nextick-args:
 *   license: MIT
 *   maintainers: cwmma <calvin.metcalf@gmail.com>
 *   version: 1.0.2
 * 
 * readable-stream:
 *   license: MIT
 *   maintainers: isaacs <isaacs@npmjs.com>, tootallnate <nathan@tootallnate.net>, rvagg <rod@vagg.org>, cwmma <calvin.metcalf@gmail.com>
 *   version: 2.0.2
 * 
 * string_decoder:
 *   license: MIT
 *   version: 0.10.31
 * 
 * through2:
 *   license: MIT
 *   author: Rod Vagg <r@va.gg>
 *   maintainers: rvagg <rod@vagg.org>, bryce <bryce@ravenwall.com>
 *   version: 2.0.0
 * 
 * type-name:
 *   license: MIT
 *   author: Takuto Wada <takuto.wada@gmail.com>
 *   maintainers: twada <takuto.wada@gmail.com>
 *   contributors: azu, Yosuke Furukawa
 *   version: 1.0.1
 * 
 * util:
 *   license: MIT
 *   author: Joyent
 *   maintainers: shtylman <shtylman@gmail.com>
 *   version: 0.10.3
 * 
 * util-deprecate:
 *   license: MIT
 *   author: Nathan Rajlich <nathan@tootallnate.net>
 *   maintainers: tootallnate <nathan@tootallnate.net>
 *   version: 1.0.1
 * 
 * xtend:
 *   licenses: MIT
 *   author: Raynos <raynos2@gmail.com>
 *   contributors: Jake Verbaten, Matt Esch
 *   version: 4.0.0
 * 
 */
(function e(t,n,r){function s(o,u){if(!n[o]){if(!t[o]){var a=typeof require=="function"&&require;if(!u&&a)return a(o,!0);if(i)return i(o,!0);var f=new Error("Cannot find module '"+o+"'");throw f.code="MODULE_NOT_FOUND",f}var l=n[o]={exports:{}};t[o][0].call(l.exports,function(e){var n=t[o][1][e];return s(n?n:e)},l,l.exports,e,t,n,r)}return n[o].exports}var i=typeof require=="function"&&require;for(var o=0;o<r.length;o++)s(r[o]);return s})({1:[function(require,module,exports){
...(your bundle continues ...)
```


HOW TO USE
---------------------------------------

by command-line

```
$ browserify main.js -p licensify > build/bundle.js 
```

or programmatically

```javascript
var browserify = require('browserify');
var licensify = require('licensify');
var fs = require('fs');
var dest = fs.createWriteStream('/path/to/bundle.js');

var b = browserify();
b.add('/path/to/your/file');
b.plugin(licensify);
b.bundle().pipe(dest)
```


#### scanBrowser option

if `scanBrowser` option is truthy, licensify scans and traverses [`browser` field](https://github.com/substack/browserify-handbook#browser-field) too.

by command-line

```
$ browserify main.js -p [ licensify --scanBrowser ] > build/bundle.js 
```

or programmatically

```javascript
var b = browserify();
b.add('/path/to/your/file');
b.plugin(licensify, {scanBrowser: true});
b.bundle().pipe(dest)
```


INSTALL
---------------------------------------

```
$ npm install --save-dev licensify
```


AUTHOR
---------------------------------------
* [Takuto Wada](http://github.com/twada)


CONTRIBUTORS
---------------------------------------
* [Okuno Kentaro](http://github.com/armorik83)
* [Ayumu Sato](https://github.com/ahomu)


LICENSE
---------------------------------------
Licensed under the [MIT](http://twada.mit-license.org/) license.


[npm-url]: https://npmjs.org/package/licensify
[npm-image]: https://badge.fury.io/js/licensify.svg

[travis-url]: http://travis-ci.org/twada/licensify
[travis-image]: https://secure.travis-ci.org/twada/licensify.svg?branch=master

[depstat-url]: https://gemnasium.com/twada/licensify
[depstat-image]: https://gemnasium.com/twada/licensify.svg

[license-url]: http://twada.mit-license.org/2014-2015
[license-image]: http://img.shields.io/badge/license-MIT-brightgreen.svg
