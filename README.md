# React Bootstrap Dialog Component

[![Build Status](https://travis-ci.org/akiroom/react-bootstrap-dialog.svg?branch=master)](https://travis-ci.org/akiroom/react-bootstrap-dialog)

It's a dialog component for react-bootstrap, easy and configurable in your React application.


## Screenshots

| Default Alert | Default Dialog | Custom Dialog |
|---------------|----------------|---------------|
| Instead of `window.alert` | Instead of `window.confirm` | Full customized |
| [![https://gyazo.com/84e315aca42ac4dbe39e51ce3451bb53](https://i.gyazo.com/84e315aca42ac4dbe39e51ce3451bb53.gif)](https://gyazo.com/84e315aca42ac4dbe39e51ce3451bb53) | [![https://gyazo.com/f8e8bfd41d9c652a55ed06a0828dc57e](https://i.gyazo.com/f8e8bfd41d9c652a55ed06a0828dc57e.gif)](https://gyazo.com/f8e8bfd41d9c652a55ed06a0828dc57e) | [![https://gyazo.com/d9c073c6c7d66c05e5398f386345f452](https://i.gyazo.com/d9c073c6c7d66c05e5398f386345f452.gif)](https://gyazo.com/d9c073c6c7d66c05e5398f386345f452) |

## Example

- See [Demos on storybook](https://akiroom.github.io/react-bootstrap-dialog/)
- The example codes are in [/src/stories/samples](https://github.com/akiroom/react-bootstrap-dialog/tree/master/src/stories/samples)

## Install 
```sh
npm i react-bootstrap-dialog --save
```

### Quick start

Step 1. Import package.

```js
import Dialog from 'react-bootstrap-dialog';
```

Step 2. Write jsx in `render` method.

```html
<Dialog ref="dialog" />
```

Step 3. Call `showAlert` method or `show` method.

```js
this.refs.dialog.showAlert('Hello Dialog!');
```

This code is full code for these steps.

```js
import React from 'react';
import {Button} from 'react-bootstrap';
import Dialog from 'react-bootstrap-dialog';

export default class SampleCode extends React.Component {
  constructor () {
    super()
    this.onClick = this.onClick.bind(this);
  }

  onClick () {
    this.refs.dialog.showAlert('Hello Dialog!');
  }

  render () {
    return (
      <div>
        <Button onClick={this.onClick}>Show alert</Button>
        <Dialog ref='dialog' />
      </div>
    )
  }
}

```

## Documents

### `Dialog`

#### setOptions(options)

Set default options for applying to all dialogs

- `options`: [Object] The parameters for default options.
  - `defaultOkLabel`: [String, Node] The default label for OK button. Default is `'OK'`.
  - `defaultCancelLabel`: [String, Node] The default label for Cancel button. Default is `'Cancel'`.
  - `primaryClassName`: [String] The class name for primary button. Default is `'btn-primary'`

##### Example

```js
Dialog.setOptions({
  defaultOkLabel: 'Yes! Yes! Yes!',
  defaultCancelLabel: 'Noooooooo!!',
  primaryClassName: 'btn-success'
});
```

#### resetOptions()

Reset default options to presets.

##### Example

```js
Dialog.resetOptions();
```

### `<Dialog />`

#### show(options)

Show dialog with choices. This is similar to `window.confirm`.

- `options`: [Object] The parameters for options.
   - `title`: [String, Node] The title of dialog.
   - `body`: [String, Node] The body of message.
   - `actions`: [DialogAction] The choices for presenting to user.
   - `bsSize`: [String] The width size for dialog. You can choose in [null, 'medium', 'large', 'small'].

##### Example

```js
this.refs.dialog.show({
  title: 'Greedings',
  body: 'How are you?',
  actions: [
    Dialog.CancelAction(),
    Dialog.OKAction()
  ],
  bsSize: 'small'
});
```

#### showAlert(body, bsSize = undefined)

Show message dialog This is similar to `window.alert`.

- `body`: [String, Node] The body of message.
- `bsSize`: [String] The width size for dialog. You can choose in [null, 'medium', 'large', 'small'].

##### Example

```js
this.refs.dialog.showAlert('Hello world!');
```

#### hide()

Hide this dialog.

##### Example

```js
this.refs.dialog.hide();
```

### `DialogAction` generators

#### Dialog.Action(label, func, className)

The customized choice for `options.actions` in `dialog.show`.

- `label`: [String, Node] The label for the button.
- `func`: [Function] The method to call when the button is clicked.
- `className`: The class name for the button.

#### Dialog.DefaultAction(label, func, className)

The default choice for `options.actions` in `dialog.show`.

- `label`: [String, Node] The label for the button.
- `func`: [Function] The method to call when the button is clicked.
- `className`: The class name for the button. (Default is `'btn-primary'`)

#### Dialog.OKAction(func)

The OK choice for `options.actions` in `dialog.show`.
It uses default ok label (`'OK'`) and default primary class (`'btn-primary'`).

- `func`: [Function] The method to call when the button is clicked.

#### Dialog.CancelAction(func)

The Cancel choice for `options.actions` in `dialog.show`.
It uses default cancel label (`'Cancel'`).

- `func`: [Function] The method to call when the button is clicked.

#### Dialog.SingleOKAction()

The OK choice to do nothing for `options.actions` in `dialog.show`.
