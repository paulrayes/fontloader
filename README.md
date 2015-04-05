# wofffontloader
Tiny and fast font loader for modern browsers

This is based on code by [Adam Beres-Deak](https://github.com/bdadam/OptimizedWebfontLoading) with modifications to make it work better for my projects.

## Usage

To use, generate CSS files for both WOFF and WOFF2 formats (fontsquirrel.com is a good place to do this) and make them available at the URL /fonts/fonts.woff.css and /fonts/woff2.css.

This Javascript file is an immediately-executing function with the arguments missing. Place this script in your document head before any external stylesheets and append the parameters of a function call with the last modified timestamp of the CSS files, like this:

	(function f(modifiedDate) {...})(1428208579)

This is best done with a build tool or dynamically generated page of some sort. The timestamp is appended for cache busting.

## Rationale

Services like Google Fonts are very useful for quickly easily fonts onto a page but require additonal DNS lookups and requests. This script allows multiple fonts to be loaded with a single request and zero additional DNS lookups, resulting in very good performance. See [Adam's blog post](http://bdadam.com/blog/loading-webfonts-with-high-performance.html) for more on why this works. I am not saving the font in local storage as that did not seem necessary to me if the server is sending the fonts with far-future expires headers.

Currently it only works in browsers that support WOFF or WOFF2, other browsers get the fallback font. For many applications this is perfectly acceptable, if not then you should find another script.

## License

MIT