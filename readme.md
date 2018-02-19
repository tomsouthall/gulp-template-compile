# gulp-template-compile

> Compile [Lo-Dash templates](http://lodash.com/docs#template) (should work with [Underscore templates](http://underscorejs.org/#template) too).

## Synopsis

This is a fork of [https://github.com/ingro/gulp-template-compile].

The major difference is the removal of the namespace functionality for replacement with a simple object assignment. This allows the output code to be wrapped in a closure where no namespacing is required.

## Example

### `gulpfile.js`

```js
var gulp = require('gulp');
var template = require('gulp-template-compile');
var concat = require('gulp-concat');

gulp.task('default', function () {
    gulp.src('src/*.html')
        .pipe(template())
        .pipe(concat('templates.js'))
        .pipe(gulp.dest('dist'));
});
```

## API

See the [Lo-Dash `_.template` docs](http://lodash.com/docs#template).


### template(options)

### options

Type: `Object`

#### options.name

Type: `Function`
Default: *Relative template path. Example: `templates/list.html`*

You can override the default behavior by supplying a function which gets the current [File](https://github.com/wearefractal/vinyl#constructoroptions) object and is expected to return the name.

Example:

```js
{
    name: function (file) {
        return 'tpl-' + file.relative;
    }
}
```

#### options.objectName
Type: `String`
Default: 'templates'

The object to which the precompiled templates will be assigned.

#### options.templateSettings
Type: `Object`
Default: null

[Lo-Dash `_.template` options](http://lodash.com/docs#template).

#### options.IIFE
Type: 'Boolean'
Default: null

Wrap each precompiled template with an [IIFE](https://en.wikipedia.org/wiki/Immediately-invoked_function_expression). If you don't need it simply set this option to `false`.

## License

MIT
