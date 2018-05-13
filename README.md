# 微信小程序 wepyjs 第三方confirmAction组件

![confirmaction](https://github.com/webdzq/wx-wpy-demo/blob/master/wpy-wx-confirmaction/confirmaction.gif)


## 说明

- 官方的actionsheet不能满足要求。所有开发了一个带提示和`确定`，`取消`组件。
- 此组件依赖于[wepyjs v1.5.2+](https://github.com/Tencent/wepy)。


## 使用

 > 有隐藏，有事件触发，比较复杂。请看示例吧

## 开发要点

> 使用了`static function` 和 `proxy`来初始化和实现事件回调

> 新版本的wepy1.7.2+ 可以使用`slot`啦.

### 安装组件
```
npm install wpy-wx-confirmaction --save-dev
```

### 引入组件
```javascript
// index.wpy
<template>
    <CofirmAction :cofirmhidden.sync="cofirmhidden" :actionTitle.sync="actionTitle" />
</template>
<script>
    import wepy from 'wepy';
    import confirmAction from 'wpy-wx-confirmaction';

    export default class Index extends wepy.page {
        components = {
            CofirmAction: confirmAction
        }

    }
</script>
```


### 调用方法（初始化默认值）
```javascript
    this.cofirmhidden = true
    this.actionTitle = '确定要删除吗'
    CofirmAction.initAction({
        confirm() {
            console.log('confirm...')
            that.cofirmhidden = false
            wx.showToast({
            title: "删除成功",
            duration: 3000
            })
        },
        cancel() {
            console.log('cancel...')
            that.cofirmhidden = false
            wx.showToast({
            title: "取消删除",
            duration: 3000
            })
        }
    })
```

## 更多说明
参考[github源码地址](https://github.com/webdzq/wpy-wx-confirmaction)。
