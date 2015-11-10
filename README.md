Sassy-Gridlover
===============

**Super easy to use Sass mixins** to establish a typographic system with modular scale and vertical rhythm.
Based on the [Gridlover app](http://www.gridlover.net/app/).

> Gridlover gives you adjustable css for font sizes, line heights and margins.
> The default css output is for body, p and h1 - h4 headings, but you can of course apply your
adjusted values to any element by editing the css later.

## First of all

Go play around with the awesome [Gridlover app](http://www.gridlover.net/app/)!

It's so much fun! :D

## Installation

Install **Sassy-Gridlover** via bower

```bash
$ bower install sassy-gridlover
```
or [Download](https://github.com/hiulit/Sassy-Gridlover/archive/master.zip) the repository and include the `sassy-gridlover` folder to your Sass directory.

## Getting started

**Sassy-Gridlover** consists of 4 configurable variables:

```scss
$sgl-base-font-size;
$sgl-base-line-height;
$sgl-base-unit;
$sgl-scale-factor;
```

and 3 mixins:

```scss
@mixin sassy-gridlover-body();
@mixin sassy-gridlover-heading();
@mixin sassy-gridlover-margins();
```

*These are the 3 functionalities of the [Gridlover app](http://www.gridlover.net/app/) that you (should) have been playing with*.

## Setup

Import `_sassy-gridlover.scss` to your main style sheet.

```scss
@import "sassy-gridlover";
```

Change the configurable variables values in `_config.scss` to your liking.

### _config.scss

```scss
// Scale factor constants.
// Don't change them ever!
$MINOR_SECOND: 1.067;
$MAJOR_SECOND: 1.125;
$MINOR_THIRD: 1.2;
$MAJOR_THIRD: 1.25;
$PERFECT_FOURTH: 1.333;
$AUGMENTED_FOURTH: 1.414;
$PERFECT_FIFTH: 1.5;
$MINOR_SIXTH: 1.6;
$GOLDEN_SECTION: 1.618;
$MAJOR_SIXTH: 1.667;
$MINOR_SEVENTH: 1.778;
$MAJOR_SEVENTH: 1.875;
$OCTAVE: 2;
$MAJOR_TENTH: 2.5;
$MAJOR_ELEVENTH: 2.667;
$MAJOR_TWELFTH: 3;
$DOUBLE_OCTAVE: 4;

// Default font size.
// Don't change it ever!
$SGL_DEFAULT_FONT_SIZE: 16;

// Configurable variables.
// Ok... You can change these variables! :D

/// Base font size
///
/// @type number
$sgl-base-font-size: 18 !default;

/// Base line height
///
/// @type number
$sgl-base-line-height: 1.2 !default;

/// Base unit
///
/// @type string
$sgl-base-unit: "pxrem" !default;

/// Scale factor
///
/// @type number
$sgl-scale-factor: $GOLDEN_SECTION !default;
```

## Mixins

By default, all the mixins will output `rem`. But you can also choose to output `px`, `em`, `pxrem`.

### Sassy-Gridlover body

To use in `<body>`.

Outputs `font-size` and `line-height`.

```scss
@mixin sassy-gridlover-body($font-size: $sgl-base-font-size, $unit: $sgl-base-unit)
```

Accepts 2 arguments:

* `$font-size`: Base font size (without unit, just a number).
* `$unit`: Unit to output (`px`, `em`, `rem`, `pxrem`).

### Sassy-Gridlover heading

To use in headings `<h1> - <h4>`.

Outputs `font-size`, `line-height`, `margin-bottom` and `margin-top`.

```scss
@mixin sassy-gridlover-heading($step, $unit: $sgl-base-unit, $base-value: $sgl-base-font-size)
```

Accepts 3 arguments:

* `$step`:
	* `<h1>` &rarr; `$step: 3`
	* `<h2>` &rarr; `$step: 2`
	* `<h3>` &rarr; `$step: 1`
	* `<h4>` &rarr; `$step: 0`
* `$unit`: Unit to output (`px`, `em`, `rem`, `pxrem`).
* `$base-value`: Optionally call with a different base font size when using em.

### Sassy-Gridlover margins

To use in `<p>`, `<ul>`, `<ol>`, `<pre>`, `<table>`, `<blockquote>`, etc.

Outputs `margin-bottom` and `margin-top`.

```scss
@mixin sassy-gridlover-margins($unit: $sgl-base-unit, $base-value: $sgl-base-font-size)
```

Accepts 2 argument:

* `$unit`: Unit to output (`px`, `em`, `rem`, `pxrem`).
* `$base-value`: Optionally call with a different base font size when using em.

## Example usage

###SCSS

```scss
@import "sassy-gridlover.scss";

body {
	@include sassy-gridlover-body($sgl-base-font-size, "rem");
}

h1 {
	@include sassy-gridlover-heading(3, "em");
}

h2 {
	@include sassy-gridlover-heading(2, "px");
}

h3 {
	@include sassy-gridlover-heading(1, "pxrem");
}

h4 {
	@include sassy-gridlover-heading(0);
}

p, ul, ol, pre, table, blockquote {
	@include sassy-gridlover-margins();
}
```

###CSS OUTPUT

```css
body {
	font-size: 1.125rem;
	line-height: 1.375rem;
}

h1 {
	font-size: 4.22222em;
	line-height: 1.15789em;
	margin-bottom: 0.28947em;
	margin-top: 0.57895em;
}

h2 {
	font-size: 47px;
	line-height: 66px;
	margin-bottom: 22px;
	margin-top: 44px;
}

h3 {
	font-size: 29px;
	line-height: 44px;
	margin-bottom: 22px;
	margin-top: 22px;
	font-size: 1.8125rem;
	line-height: 2.75rem;
	margin-bottom: 1.375rem;
	margin-top: 1.375rem;
}

h4 {
	font-size: 18px;
	line-height: 22px;
	margin-bottom: 22px;
	margin-top: 22px;
	font-size: 1.125rem;
	line-height: 1.375rem;
	margin-bottom: 1.375rem;
	margin-top: 1.375rem;
}

p, ul, ol, pre, table, blockquote {
	margin-bottom: 22px;
	margin-top: 22px;
	margin-bottom: 1.375rem;
	margin-top: 1.375rem;
}
```

## To-Do

* Support em. There's a [branch](https://github.com/hiulit/Sassy-Gridlover/tree/em-support) for that matter.

## Changelog

### v2.0.0 (November 11th 2015)

**NOTE:** This release contains breaking changes!

* Added [em support](https://github.com/hiulit/Sassy-Gridlover/pull/7).
* Added @param {string} $unit [$sgl-base-unit] - Unit to output
* ~~@param {Boolean} $rem [false] - Outputs rem units if `true`~~ **Deprecated**

### v1.2.0 (February 25th 2015)

* Upgraded to [SassDoc](http://sassdoc.com/) v2.1.0

### v1.1.0 (October 20th 2014)

* Added [SassDoc](http://sassdoc.com/) documentation [#6](https://github.com/hiulit/Sassy-Gridlover/issues/6).
* Applied naming conventions to constants [#5](https://github.com/hiulit/Sassy-Gridlover/issues/5).
* Added `pow()` function for [Compass](http://compass-style.org/reference/compass/helpers/math/), [Sassy-math](https://github.com/Team-Sass/Sassy-math]), etc. [#4](https://github.com/hiulit/Sassy-Gridlover/issues/4)
* Changed strings for lengths [#3](https://github.com/hiulit/Sassy-Gridlover/issues/3)
* Added `!default` to configurable variables [#2](https://github.com/hiulit/Sassy-Gridlover/issues/2)

### v1.0.0 (October 6th 2014)

* Released stable version.
* Added bower installation support.

### v0.1.0 (September 2nd 2014)

* Initial commit.

## Inspiration and alternatives

* [Gridlover app](http://www.gridlover.net/app/) - The tool to establish a typographic system with modular scale and vertical rhythm.
* [Knife](https://github.com/Pushplaybang/knife) - Nail vertical rhythm, modular scale, and REMs like a boss with this simple set of SASS/SCSS variables, functions and mixins.
* [gridlover-mixin](https://github.com/sevenupcan/gridlover-mixin) - A mixin to generate modular scale and vertical rhythm for your typography.

## Credits

Thanks to:

* [Gridlover app](http://www.gridlover.net/app/) - Created by [Tuomas Jomppanen](http://twitter.com/tuomasj) & [Ville Vanninen](http://twitter.com/sakamies).
* [Sassy-math](https://github.com/Team-Sass/Sassy-math) [&copy; 2012](https://github.com/Team-Sass/Sassy-math#license) - For the `@function exponent()`. Created by [Sam Richard](https://github.com/Snugug), [Mario Valencia](https://github.com/sultancillo) and [Scott Kellum](https://github.com/scottkellum)
* Marc Mintel ([@marcmintel](https://twitter.com/marcmintel)) for his amazing article on how to [Write Sass plugins like a pro](https://medium.com/@marcmintel/write-sass-plugins-like-a-pro-c765ecf3af27).
* Hugo Giraudel ([@hugogiraudel](https://twitter.com/hugogiraudel)) for helping with issues and [SassDoc](http://sassdoc.com/).
* Walid Mokrani ([@walmokrani](https://github.com/walmokrani)) for helping with [adding em support](https://github.com/hiulit/Sassy-Gridlover/pull/7).

## Unlicense

This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or
distribute this software, either in source code form or as a compiled
binary, for any purpose, commercial or non-commercial, and by any
means.

In jurisdictions that recognize copyright laws, the author or authors
of this software dedicate any and all copyright interest in the
software to the public domain. We make this dedication for the benefit
of the public at large and to the detriment of our heirs and
successors. We intend this dedication to be an overt act of
relinquishment in perpetuity of all present and future rights to this
software under copyright law.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR
OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

For more information, please refer to <http://unlicense.org/>