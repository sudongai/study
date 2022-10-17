---
sidebar: auto
sidebarDepth: 2
---

<!-- ## css笔记 -->
<!-- ------------------ -->
## 刨析toolTip超长显示... 不超长不显示原理
要让文本超过长度后，截取显示并附上省略号，可以通过如下的css代码实现：

```js
 text-overflow: ellipsis;
 overflow: hidden;
 white-space: nowrap;
 width:100px;
```
有时候，我们需要根据文本是否省略做一些别的事情，例如显示一个展开按钮。现在是CSS控制文本省略了，如何检测到呢？
废话不多说，直接通过文本元素的clientWidth和scrollWidth来检测。
clientWidth是元素的可视宽度。scrollWidth是元素的滚动宽度，包括了滑动条边框和被隐藏的内容宽度。因此可以直接判断clientWidth和scrollWidth的大小，来确定是否文本被省略了。代码如下：

```js
/* 文字是否被省略*/
    function isElipsis(id) {
        var clientWidth = document.getElementById(id).clientWidth;
        var scrollWidth = document.getElementById(id).scrollWidth;

        return (clientWidth < scrollWidth); // 说明文字被省略了
    }
```