## Getting Started

`ionic serve`

The `ionic serve` command compiles your ES6 files to ES5, your Sass files to CSS, bundles it all up for you, opens up a browser window and serves your app locally.  After the initial build it will watch for changes and automatically rebuild and reload.  The build output can be configured in your `ionic.config.js` file (which will be autogenerated by `ionic serve` if it doesn't exist yet).

#### Updating Ionic
When you start your project with `ionic start`, the latest version of `ionic-framework` is installed automatically. To update your ionic version in an existing project, run `npm install --save ionic-framework@latest`. This will install the latest version of `ionic-framework` published to npm, and save it in your `package.json` file so if you are checking your project in to version control the correct version of the framework will be installed by [`npm install`](https://docs.npmjs.com/cli/install).

#### Developing Against Unstable Master
- THIS IS NOT UPDATING YOUR APP. THIS IS FOR DEVELOPING AGAINST THE UNSTABLE MASTER BRANCH, WHICH WE DO NOT RECOMMEND. SEE [Updating Ionic](#updating-ionic) FOR INSTRUCTIONS ON UPDATING TO THE LATEST VERSION OF THE FRAMEWORK. To develop against a local version of ionic-framework (master) you'll need to do the following:
```bash
# if you haven't already, clone the ionic2 repo:
$ git clone https://github.com/driftyco/ionic2.git
$ cd ionic2
$ npm install
$ gulp src # build the source files
$ npm link

# now go to your app directory
$ cd /Users/Ionitron/git/MyIonic2App
$ npm link ionic-framework
```
And then update your [`webpack.config.js`](https://github.com/driftyco/ionic2-app-base/blob/master/webpack.config.js#L68) file by uncommenting the lines for local development:
```js
resolve: {
  modulesDirectories: [
    "node_modules",
    "node_modules/ionic-framework/node_modules", 
    "node_modules/ionic-framework/dist/src/es5/common", 
    "node_modules/ionic-framework/dist/js", 

    "dist/src/es5/common" // <--- Uncomment me  
  ],
}
```
Update the ionic2 [`gulpfile.js #L141`](https://github.com/driftyco/ionic2/blob/master/gulpfile.js#L141) to this in order to use `gulp watch` and make changes to the ionic2 repo:
```js
gulp.start('transpile.common');
```


### Missing Ionic 1 features

We are currently working on completing a few core Ionic 1 features:

- Collection repeat (known as Virtual Scrolling in v2) is not quite ready

### Current Angular 2 known issues:

- Angular 2 is still in alpha and is not production ready
- Angular team has first focused on developing what the core of Angular 2 "is"
- Angular 2 filesize has not been optimized for minification yet
- Angular 2 bootstrap time has not been optimized yet
- As Angular 2 reaches beta there will be significant performance improvements


### ES6/Typescript

- Ionic's source is written using [Typescript](http://www.typescriptlang.org/)
- Ionic apps can be written in ES6 or TypeScript
- Typescript is an optional feature to be used at the developers discretion
- Ionic 2 starters come with the necessary build tools to transpile both ES6 and Typescript


### CSS Attribute Selectors:

- Simple
- Smaller markup
- Easier to read and understand
- [Not an issue](https://twitter.com/paul_irish/status/311610425617838081) for today's mobile browsers
- No performance impacts have been found
