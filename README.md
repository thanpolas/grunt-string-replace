# grunt-string-replace [![Build Status](https://travis-ci.org/erickrdch/grunt-string-replace.png?branch=0.2.0rc1)](https://travis-ci.org/erickrdch/grunt-string-replace)

Replaces strings on files by using string or regex patterns. Attempts to be a [String.prototype.replace](http://www.ecma-international.org/ecma-262/5.1/#sec-15.5.4.11) adapter task for your grunt project.

## Getting Started
To install this grunt plugin on your project simply do: `npm install grunt-string-replace`

Then add this line to your project's `Gruntfile.js`:

```javascript
grunt.loadNpmTasks('grunt-string-replace');
```

[grunt]: http://gruntjs.com/

## Documentation

### Configuration

Inside your `Gruntfile.js` file add a section named `string-replace`. This section specifies the files to edit, destinations, patterns and replacements.

#### Parameters

##### files ```object```

This defines what files this task will edit and must follow [Gruntfile Files mapping](https://github.com/gruntjs/grunt/wiki/Configuring-tasks).

##### options ```object```

This controls how this task operates and should contain key:value pairs, see options below.

#### Options

##### replacements ```array```

This option will hold all your pattern/replacement pairs. A pattern/replacement pair should contain key:value pairs containing:

* pattern ```string``` or ```regex```
* replacement ```string```

``` javascript
options: {
  replacements: [{
    pattern: /\/(asdf|qwer)\//ig,
    replacement: "'$1'"
  }, {
    pattern: ",",
    replacement: ";"
  }]
}
```

###### Note

If the pattern is a string, only the first occurrence will be replaced, as stated on [String.prototype.replace](http://www.ecma-international.org/ecma-262/5.1/#sec-15.5.4.11).

#### Config Example

``` javascript
"string-replace": {
  dist: {
    files: {
      "path/to/directory/": "path/to/source/*", // includes files in dir
      "path/to/directory/": "path/to/source/**", // includes files in dir and subdirs
      "path/to/project-<%= pkg.version %>/": "path/to/source/**", // variables in destination
      "path/to/directory/": ["path/to/sources/*.js", "path/to/more/*.js"], // include JS files in two diff dirs
      "path/to/filename.ext": "path/to/source.ext"
    },
    options: {
      replacements: [{
        pattern: /\/(asdf|qwer)\//ig,
        replacement: "'$1'"
      }, {
        pattern: ",",
        replacement: ";"
      }]
    }
  }
}
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [grunt][grunt].

## Release History
0.2.0
  - Added Support for grunt 0.4.0. This version will not support grunt 0.3.x, if you need to use it then ```npm install grunt-string-replace@0.1```

0.1.1-1
  - Added Clean task (and dev dependency) to remove test generated file before testing
  - Added Sublime Text project files and test generated file to npm ignore list

0.1.1
  - Fix dependency with grunt-lib-contrib

0.1.0-1
  - Fixed a typo on package.json description
  - Added a note about string pattern behavior

0.1.0
  - Initial release

## License
Copyright (c) 2012 Erick Ruiz de Chavez
Licensed under the MIT license.
