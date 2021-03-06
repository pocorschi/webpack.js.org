---
title: SourceMapDevToolPlugin
contributors:
  - johnnyreilly
  - simon04
related:
  - title: Building Source Maps
    url: https://survivejs.com/webpack/building/source-maps/#-sourcemapdevtoolplugin-and-evalsourcemapdevtoolplugin-
---

This plugin enables more fine grained control of source map generation. It is an alternative to the [`devtool`](/configuration/devtool/) configuration option.

```javascript
new webpack.SourceMapDevToolPlugin(options)
```


## Options

The following options are supported:

- `test` (`string|regex|array`): Include source maps for modules based on their extension (defaults to `.js` and `.css`).
- `include` (`string|regex|array`): Include source maps for module paths that match the given value.
- `exclude` (`string|regex|array`): Exclude modules that match the given value from source map generation.
- `filename` (`string`): Defines the output filename of the SourceMap (will be inlined if no value is provided).
- `append` (`string`): Appends the given value to the original asset. Usually the `#sourceMappingURL` comment. `[url]` is replaced with a URL to the source map file. `false` disables the appending.
- `moduleFilenameTemplate` (`string`): See [`output.devtoolModuleFilenameTemplate`](/configuration/output/#output-devtoolmodulefilenametemplate).
- `fallbackModuleFilenameTemplate` (`string`): See link above.
- `module` (`boolean`): Indicates whether loaders should generate source maps (defaults to `true`).
- `columns` (`boolean`): Indicates whether column mappings should be used (defaults to `true`).
- `lineToLine` (`object`): Simplify and speed up source mapping by using line to line source mappings for matched modules.**

The `lineToLine` object allows for the same `test`, `include`, and `exclude` options described above.

T> Setting `module` and/or `columns` to `false` will yield less accurate source maps but will also improve compilation performance significantly.


## Usage: Exclude Vendor Maps

The following code would exclude source maps for any modules in the `vendor.js` bundle:

```javascript
new webpack.SourceMapDevToolPlugin({
  filename: '[name].js.map',
  exclude: ['vendor.js']
})
```
