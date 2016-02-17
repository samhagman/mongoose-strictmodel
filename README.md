# mongoose-strictmodel

> Mongoose plugin that forces Mongoose queries to respect your Mongoose models.

## About

The plugin adds pre-hooks to the Mongoose query functions listed below:

- find
- findOne
- findOneAndRemove
- findOneAndUpdate
- update
- count

These pre-hooks will look at the query parameters and transform queries to only
ever return fields that are defined in your models even if they are in the data
inside your MongoDB instance.  This is especially useful for when you do not
define specific fields to return and you get more fields than your Model knows
about.  It is also helpful for making sure that you keep your Mongoose models
up-to-date with the data on the server.


## Options

This plugin takes an options object as an optional second parameter;
there are currently two configurable fields:

> <Boolean> allowNonModelQueryParameters

This option allows **query parameters** that are not on the model to be silently
ignored by the plugin.  The plugin will still not return any fields not on the
model, but it will no longer throw an error.  False by default.

> <Boolean> allowNonModelSelectionParameters

This option allows **selection parameters** that are not on the model to be silently
ignored by the plugin.  The plugin will still not return any fields not on the
model, but it will no longer throw an error.  False by default.

## Roadmap

- [x] Pre-hooks on all functions that support them
- [ ] Post-hooks on all functions that support them
- [ ] Custom `.toJSON()` type function that returns only Model fields
