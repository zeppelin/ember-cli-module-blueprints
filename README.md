# Ember CLI Module Blueprints

**WARNING:** *This addon is experimental and rely on features that are not yet default in Ember CLI for a reason. Be prepared to update your app if the `import` names generated by this addon change.*

The goal of this addon is to provide blueprints that contain `import` statements targeting modules directly, instead of `import`ing `Ember`, and then accessing the entity from the `Ember` object.

For example, the current component blueprint:

```js
import Ember from 'ember';

export default Ember.Component.extend({
});
```

Becomes:

```js
import Component from 'ember-component';

export default Component.extend({
});
```

Blueprints affected: component, controller, helper, mixin, route, service, test-helper.

For the full list of currently available ES6 exports, see [the list of ES6 module shims](https://github.com/ember-cli/ember-cli-shims/blob/master/app-shims.js). Using these modules let you `import` most of Ember's classes and functions, for example your app code can look like this:

```js
import Component from 'ember-component';
import computed from 'ember-computed';
import service from 'ember-service/inject';

export default Component.extend({
  foo: service(), // Same as: `Ember.inject.service()`
  hello: computed('foo.bar', function() { // Same as: `Ember.computed`
    return this.get('foo.bar');
  })
});
```

## Installation

```
ember install ember-cli-module-blueprints
```

## Running Tests

* `npm test` (Runs `ember try:testall` to test your addon against multiple Ember versions)
* `ember test`
* `ember test --server`

## Building

* `ember build`

For more information on using ember-cli, visit [http://ember-cli.com/](http://ember-cli.com/).
