React Unsafe React Hooks that need to be migrated.
1. componentWillMount
2. componentWillReceiveProps
3. componentWillUpdate

## UNSAFE_componentWillReceiveProps
__Description__: method invoked when props are updated
__Migration__: There are two parts to this, side-effects and state

1. For side-effects, you should use _componentDidUpdate_.  You may also set state but must have the right condition to avoid infinite loop
2. For component level state, you should use static getDerivedStateFromProps. However, it's a static method that does not have access to this.

## UNSAFE_componentWillUpdate
__Description__: Very similar to component will update, except it will happen just before render. Because of that you can't use setState. Can be useful to manipulate component just before it receives new props/state

__Migration__: According to react docs, you can use just convert it to componentDidUpdate(). However, componentWillUpdate is different from componentDidUpdate because it is invoked AFTER. 

It might be useful to execute some code after setting the state.

```javascript
this.setState({
    someState: obj
}, () => {
    this.afterSetStateFinished();
});
```


### Useful Resources
https://itnext.io/react17-or-how-to-get-rid-of-componentwillreceiveprops-c91f9a6f6f03
https://hackernoon.com/hn-images/1*sn-ftowp0_VVRbeUAFECMA.png
