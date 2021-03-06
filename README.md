# react-adaptive [![NPM](https://img.shields.io/npm/v/react-adaptive.svg)](https://www.npmjs.com/package/react-adaptive) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

A Higher Order Component (HOC) allowing you to adapt your component display according to its own size and integrate you website with adaptive design.

## Information

<table>
  <tr>
    <td>Package</td>
    <td>react-adaptive</td>
  </tr>
  <tr>
    <td>Description</td>
    <td>Element size in react for adaptive design</td>
  </tr>
  <tr>
    <td>Example (basic for now)</td>
    <td>https://lokymil.github.io/react-adaptive/</td>
  </tr>
</table>

## Install
```bash
npm install --save react-adaptive
```


## Usage

### Using withAdaptive HOC

In that case, you have to define a function receiving the size of the component and returning expected component according to your own process.

```js
import React, { Component } from 'react';
import { withAdaptive } from 'react-adaptive';

class LargeComponent extends Component {
  render() {
    return (
      <div>
        My large component {this.props.name}
      </div>
    );
  }
}

class MediumComponent extends Component {
  render() {
    return (
      <div>
        My medium component {this.props.name}
      </div>
    );
  }
}

class SmallComponent extends Component {
  render() {
    return (
      <div>
        My small component {this.props.name}
      </div>
    );
  }
}

const mapSizeToComponent = size => props => {
  if (size.width < 400) {
    return <SmallComponent {...props} />;
  }

  if (size.width < 700) {
    return <MediumComponent {...props} />;
  }

  return <LargeComponent {...props} />;
};

export default withAdaptive({ mapSizeToComponent });
```

### Using withBreakpoint HOC

In that case, you have to define a set of breakpoints, up to 7, and a set of associated components. You can define an optionnal default Component.  
Breakpoints name :
<table>
  <tr>
  </tr>
</table>

```js
import React, { Component } from 'react';
import { withBreakpoints, breakpoints } from 'react-adaptive';

class LargeComponent extends Component {
  render() {
    return (
      <div>My large component components.name}</div>
    );
  }
}

class MediumComponent extends Component {
  render() {
    return (
      <div>My medium component components.name}</div>
    );
  }
}

class SmallComponent extends Component {
  render() {
    return (
      <div>My small component components.name}</div>
    );
  }
}

const components = {
  [breakpoints.large]: LargeComponent,
  [breakpoints.medium]: MediumComponent,
  [breakpoints.small]: SmallComponent
};

const breakPoints = {
  [breakpoints.large]: 1000,
  [breakpoints.medium]: 700,
  [breakpoints.small]: 400
};

export default withBreakpoints(breakPoints)({
  components,
  defaultComponent: LargeComponent
});
```

### Using withSize HOC

In that case, your component will have an additionnal props as: 
```js
size = { width: `current component width` }
```

```js
import React from 'react';
import { withSize } from 'react-adaptive';

const MyComponent = ({ size }) => (<div>My own size is {size.width}</div>);

export default withSize(MyComponent);
```

## License

MIT © [Lokymil](https://github.com/Lokymil)
