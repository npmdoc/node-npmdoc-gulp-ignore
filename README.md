# api documentation for  [gulp-ignore (v2.0.2)](https://github.com/robrich/gulp-ignore)  [![npm package](https://img.shields.io/npm/v/npmdoc-gulp-ignore.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-gulp-ignore) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-gulp-ignore.svg)](https://travis-ci.org/npmdoc/node-npmdoc-gulp-ignore)
#### Include or exclude gulp files from the stream based on a condition

[![NPM](https://nodei.co/npm/gulp-ignore.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/gulp-ignore)

[![apidoc](https://npmdoc.github.io/node-npmdoc-gulp-ignore/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-gulp-ignore/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-gulp-ignore/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-gulp-ignore/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Rob Richardson",
        "url": "http://robrich.org/"
    },
    "bugs": {
        "url": "https://github.com/robrich/gulp-ignore/issues"
    },
    "dependencies": {
        "gulp-match": "^1.0.3",
        "through2": "^2.0.1"
    },
    "description": "Include or exclude gulp files from the stream based on a condition",
    "devDependencies": {
        "jshint": "^2.9.4",
        "mocha": "^3.1.2",
        "should": "^11.1.1"
    },
    "directories": {},
    "dist": {
        "shasum": "5c2ea2a0a4402e0ab4a2bcd12efd9295344d78f2",
        "tarball": "https://registry.npmjs.org/gulp-ignore/-/gulp-ignore-2.0.2.tgz"
    },
    "engines": {
        "node": ">= 0.10.0"
    },
    "gitHead": "7b085b61823820809f3dc2f3875d93d89ea3cb92",
    "homepage": "https://github.com/robrich/gulp-ignore",
    "keywords": [
        "gulpplugin",
        "filter",
        "minimatch",
        "include",
        "exclude",
        "gulp-filter"
    ],
    "license": "MIT",
    "main": "./index.js",
    "maintainers": [
        {
            "name": "robrich"
        }
    ],
    "name": "gulp-ignore",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git://github.com/robrich/gulp-ignore.git"
    },
    "scripts": {
        "test": "mocha && jshint ."
    },
    "version": "2.0.2"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module gulp-ignore](#apidoc.module.gulp-ignore)
1.  [function <span class="apidocSignatureSpan"></span>gulp-ignore (condition, minimatchOptions)](#apidoc.element.gulp-ignore.gulp-ignore)
1.  [function <span class="apidocSignatureSpan">gulp-ignore.</span>exclude (condition, minimatchOptions)](#apidoc.element.gulp-ignore.exclude)
1.  [function <span class="apidocSignatureSpan">gulp-ignore.</span>include (condition, minimatchOptions)](#apidoc.element.gulp-ignore.include)
1.  [function <span class="apidocSignatureSpan">gulp-ignore.</span>toString ()](#apidoc.element.gulp-ignore.toString)

#### [module gulp-ignore.exclude](#apidoc.module.gulp-ignore.exclude)
1.  [function <span class="apidocSignatureSpan">gulp-ignore.</span>exclude (condition, minimatchOptions)](#apidoc.element.gulp-ignore.exclude.exclude)
1.  [function <span class="apidocSignatureSpan">gulp-ignore.exclude.</span>include (condition, minimatchOptions)](#apidoc.element.gulp-ignore.exclude.include)



# <a name="apidoc.module.gulp-ignore"></a>[module gulp-ignore](#apidoc.module.gulp-ignore)

#### <a name="apidoc.element.gulp-ignore.gulp-ignore"></a>[function <span class="apidocSignatureSpan"></span>gulp-ignore (condition, minimatchOptions)](#apidoc.element.gulp-ignore.gulp-ignore)
- description and source-code
```javascript
gulp-ignore = function (condition, minimatchOptions){
	return through.obj(function (file, enc, callback) {
		if (!gulpmatch(file, condition, minimatchOptions)) {
			this.push(file);
		}
		return callback();
	});
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-ignore.exclude"></a>[function <span class="apidocSignatureSpan">gulp-ignore.</span>exclude (condition, minimatchOptions)](#apidoc.element.gulp-ignore.exclude)
- description and source-code
```javascript
exclude = function (condition, minimatchOptions){
	return through.obj(function (file, enc, callback) {
		if (!gulpmatch(file, condition, minimatchOptions)) {
			this.push(file);
		}
		return callback();
	});
}
```
- example usage
```shell
...
var jshint = require('gulp-jshint');

var condition = './gulpfile.js';

gulp.task('task', function() {
  gulp.src('./**/*.js')
    .pipe(jshint())
    .pipe(gulpIgnore.exclude(condition))
    .pipe(uglify())
    .pipe(gulp.dest('./dist/'));
});
'''

Run JSHint on everything, remove gulpfile from the stream, then uglify and write everything else.
...
```

#### <a name="apidoc.element.gulp-ignore.include"></a>[function <span class="apidocSignatureSpan">gulp-ignore.</span>include (condition, minimatchOptions)](#apidoc.element.gulp-ignore.include)
- description and source-code
```javascript
include = function (condition, minimatchOptions){
	return through.obj(function (file, enc, callback) {
		if (gulpmatch(file, condition, minimatchOptions)) {
			this.push(file);
		}
		return callback();
	});
}
```
- example usage
```shell
...
var jshint = require('gulp-jshint');

var condition = './public/**.js';

gulp.task('task', function() {
  gulp.src('./**/*.js')
    .pipe(jshint())
    .pipe(gulpIgnore.include(condition))
    .pipe(uglify())
    .pipe(gulp.dest('./dist/'));
});
'''

Run JSHint on everything, filter to include only files from in the public folder, then uglify and write them.
...
```

#### <a name="apidoc.element.gulp-ignore.toString"></a>[function <span class="apidocSignatureSpan">gulp-ignore.</span>toString ()](#apidoc.element.gulp-ignore.toString)
- description and source-code
```javascript
toString = function () {
    return toString;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.gulp-ignore.exclude"></a>[module gulp-ignore.exclude](#apidoc.module.gulp-ignore.exclude)

#### <a name="apidoc.element.gulp-ignore.exclude.exclude"></a>[function <span class="apidocSignatureSpan">gulp-ignore.</span>exclude (condition, minimatchOptions)](#apidoc.element.gulp-ignore.exclude.exclude)
- description and source-code
```javascript
exclude = function (condition, minimatchOptions){
	return through.obj(function (file, enc, callback) {
		if (!gulpmatch(file, condition, minimatchOptions)) {
			this.push(file);
		}
		return callback();
	});
}
```
- example usage
```shell
...
var jshint = require('gulp-jshint');

var condition = './gulpfile.js';

gulp.task('task', function() {
  gulp.src('./**/*.js')
    .pipe(jshint())
    .pipe(gulpIgnore.exclude(condition))
    .pipe(uglify())
    .pipe(gulp.dest('./dist/'));
});
'''

Run JSHint on everything, remove gulpfile from the stream, then uglify and write everything else.
...
```

#### <a name="apidoc.element.gulp-ignore.exclude.include"></a>[function <span class="apidocSignatureSpan">gulp-ignore.exclude.</span>include (condition, minimatchOptions)](#apidoc.element.gulp-ignore.exclude.include)
- description and source-code
```javascript
include = function (condition, minimatchOptions){
	return through.obj(function (file, enc, callback) {
		if (gulpmatch(file, condition, minimatchOptions)) {
			this.push(file);
		}
		return callback();
	});
}
```
- example usage
```shell
...
var jshint = require('gulp-jshint');

var condition = './public/**.js';

gulp.task('task', function() {
  gulp.src('./**/*.js')
    .pipe(jshint())
    .pipe(gulpIgnore.include(condition))
    .pipe(uglify())
    .pipe(gulp.dest('./dist/'));
});
'''

Run JSHint on everything, filter to include only files from in the public folder, then uglify and write them.
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
