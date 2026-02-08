<!--

@license Apache-2.0

Copyright (c) 2025 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# rangeBy

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Calculate the [range][range] of a one-dimensional ndarray via a callback function.

<section class="intro">

The [**range**][range] is defined as the difference between the maximum and minimum values.

</section>

<!-- /.intro -->



<section class="usage">

## Usage

```javascript
import rangeBy from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-base-ndarray-range-by@v0.1.1-esm/index.mjs';
```

#### rangeBy( arrays, clbk\[, thisArg ] )

Computes the [range][range] of a one-dimensional ndarray via a callback function.

```javascript
import ndarray from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-base-ctor@esm/index.mjs';

function clbk( value ) {
    return value * 2.0;
}

var xbuf = [ 1.0, 3.0, 4.0, 2.0 ];
var x = new ndarray( 'generic', xbuf, [ 4 ], [ 1 ], 0, 'row-major' );

var v = rangeBy( [ x ], clbk );
// returns 6.0
```

The function has the following parameters:

-   **arrays**: array-like object containing a one-dimensional input ndarray.
-   **clbk**: callback function.
-   **thisArg**: callback execution context (_optional_).

The invoked callback is provided three arguments:

-   **value**: current array element.
-   **idx**: current array element index.
-   **array**: input ndarray.

To set the callback execution context, provide a `thisArg`.

```javascript
import ndarray from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-base-ctor@esm/index.mjs';

function clbk( value ) {
    this.count += 1;
    return value * 2.0;
}

var xbuf = [ 1.0, 3.0, 4.0, 2.0 ];
var x = new ndarray( 'generic', xbuf, [ 4 ], [ 1 ], 0, 'row-major' );
var ctx = {
    'count': 0
};

var v = rangeBy( [ x ], clbk, ctx );
// returns 6.0

var count = ctx.count;
// returns 4
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   If provided an empty one-dimensional ndarray, the function returns `NaN`.
-   A provided callback function should return a numeric value.
-   If a provided callback function does not return any value (or equivalently, explicitly returns `undefined`), the value is **ignored**.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="module">

import discreteUniform from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-array-discrete-uniform@esm/index.mjs';
import ndarray from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-base-ctor@esm/index.mjs';
import ndarray2array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-to-array@esm/index.mjs';
import rangeBy from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-base-ndarray-range-by@v0.1.1-esm/index.mjs';

function clbk( value ) {
    return value * 2.0;
}

var xbuf = discreteUniform( 10, -50, 50, {
    'dtype': 'generic'
});
var x = new ndarray( 'generic', xbuf, [ xbuf.length ], [ 1 ], 0, 'row-major' );
console.log( ndarray2array( x ) );

var v = rangeBy( [ x ], clbk );
console.log( v );

</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/stats-base-ndarray-range-by.svg
[npm-url]: https://npmjs.org/package/@stdlib/stats-base-ndarray-range-by

[test-image]: https://github.com/stdlib-js/stats-base-ndarray-range-by/actions/workflows/test.yml/badge.svg?branch=v0.1.1
[test-url]: https://github.com/stdlib-js/stats-base-ndarray-range-by/actions/workflows/test.yml?query=branch:v0.1.1

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-base-ndarray-range-by/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-base-ndarray-range-by?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-base-ndarray-range-by.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-base-ndarray-range-by/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/stats-base-ndarray-range-by/tree/deno
[deno-readme]: https://github.com/stdlib-js/stats-base-ndarray-range-by/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/stats-base-ndarray-range-by/tree/umd
[umd-readme]: https://github.com/stdlib-js/stats-base-ndarray-range-by/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/stats-base-ndarray-range-by/tree/esm
[esm-readme]: https://github.com/stdlib-js/stats-base-ndarray-range-by/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/stats-base-ndarray-range-by/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/stats-base-ndarray-range-by/main/LICENSE

[range]: https://en.wikipedia.org/wiki/Range_%28statistics%29

</section>

<!-- /.links -->
