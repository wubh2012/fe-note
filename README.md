# 前端笔记

## 在线书籍文档

[Web开发者应该掌握的CSS tricks](https://lhammer.cn/You-need-to-know-css/#/zh-cn/)

[JavaScript 教程 - 阮一峰](https://wangdoc.com/javascript/index.html)

[ECMAScript 6 入门 - 阮一峰](http://es6.ruanyifeng.com/)

[JavaScript Promise迷你书（中文版）](http://liubin.org/promises-book/)

[Learn X in Y Minutes Program](https://learnxinyminutes.com/)

[面试图谱 InterviewMap](https://yuchengkai.cn/docs/)

[jQuery 在线手册](http://hemin.cn/jq/) [jQuery API 中文文档](https://www.jquery123.com/)

## HTML

[RGB颜色值与16进制颜色转换](https://www.sioe.cn/yingyong/yanse-rgb-16/)

[Can I Use](https://caniuse.com/)

## CSS工具箱

[CSS3 Keyframes Animation Generator](http://cssanimate.com/)

[CSS渐变颜色生成器](http://www.colorzilla.com/gradient-editor/) 或  http://www.css3developer.com/css3generator/gradient-css.html

[Box Shadow CSS Generator | CSSmatic](https://www.cssmatic.com/box-shadow) 还有 Border Radius 

[CSS属性可视化工具](https://cssreference.io/)

[Animation.css 动画库](https://daneden.github.io/animate.css/)

[CSS 三角形](http://apps.eky.hk/css-triangle-generator/zh-hant)

[多边形CSS](https://bennettfeely.com/clippy/)

[在线CSStoSASS](http://css2sass.w3ci.com/)

### 布局练习

[学习CSS布局](http://zh.learnlayout.com/)

[Flexbox Froggy - 一个用来学CSS flexbox的游戏](http://flexboxfroggy.com/#zh-cn)

[Flexbox 练习游戏](http://www.flexboxdefense.com/)

## 找图片图标
[图标](https://www.iconfont.cn/)

[背景图片](http://www.hituyu.com/)

[dribbbel](https://dribbble.com)

## UI框架库

* [Ant Design](https://ant.design/index-cn)
* [ElementUI 组件库](http://element-cn.eleme.io/#/zh-CN/component/installation)
* [Bootstrap](https://www.bootcss.com/)

## JS库

| 名称                                      | 说明                  |
| ----------------------------------------- | --------------------- |
| marked.js                                 | 将 markdown 转成 html |
| Prism.js                                  | 代码美化插件          |
| particles.js                              | 粒子动画库            |
| [typer.js](https://steven.codes/typerjs/) | 文字输入特效          |
|                                           |                       |

## 伪类

```
:visited	已访问	
:active	选定
:link	未访问	
:hover	悬停
```

## 定位 position

```
static		默认
relative	相对定位
absolute	相对 父元素 绝对定位,position 值不是 static 的元素。
fixed		相对 浏览器 绝对定位
```

## JS 标准库

### 字符串 String

| 方法                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| **[slice( )](<https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/slice>)** | 返回 切片                    |
| includes( str )                                              | 检查 是否包含 str 返回 bool  |
| trim( )                                                      | 去除首尾空格                 |
| split( str )                                                 | 以 str 分割字符串 返回 array |
| toLowerCase()                                                | 字母转小写                   |
| toUpperCase()                                                | 字母转大写                   |
| indexOf( str )                                               | 查找 是否包含 str 返回 下标  |
| [replace](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace)( pattern, str ) 原字符串不会改变 | 替换 pattern 为 str          |

```javascript
var str1 = 'The morning is upon us.';
var str2 = str1.slice(4, -2);
console.log(str2); // OUTPUT: morning is upon u


// 正则表达式包含有全局替换(g)和忽略大小写(i)的选项
var re = /apples/gi;
var str = "Apples are round, and apples are juicy.";
var newstr = str.replace(re, "oranges");

console.log(newstr);// oranges are round, and oranges are juicy.

// 交换字符串中的两个单词
var re = /(\w+)\s(\w+)/;
var str = "John Smith";
var newstr = str.replace(re, "$2, $1");
// Smith, John
console.log(newstr);

// 用行内函数修改匹配到的字符
function styleHyphenFormat(propertyName) {
  function upperToHyphenLower(match) {
    return '-' + match.toLowerCase();
  }
  return propertyName.replace(/[A-Z]/g, upperToHyphenLower);
}
styleHyphenFormat('borderTop') // 返回'border-top'
```

### Math

| 属性       | 说明                    | 举例          |
| ---------- | ----------------------- | ------------- |
| floor( x ) | 返回 <= x 整数 向下取整 | ( -2.1 ) = -3 |
| ceil( x )  | 返回 >= x 整数 向上取整 | ( -2.1 ) = -2 |
| round( x ) | 返回 x 四舍五入         | ( 5.4 ) = 5   |
| abs( x )   | 返回 x 绝对值           |               |
| random( )  | 生成 0 - 1 随机小数     |               |

### Date

```javascript
let time = function(z) {
    if (z === undefined) { z = new Date() }
    let x = z.toString()
    // ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday','Friday', 'Saterday']
    let zh     = '天一二三四五六'
    let Year   = x.slice(11,15)
    let Month  = z.getMonth() + 1
    let Day    = x.slice(8,10)
    let Hour   = x.slice(16,18)
    let Minute = x.slice(19,21)
    let Second = x.slice(22,24)
    let Week   = zh[z.getDay()]
    if (String(Month).length === 1) {
        Month = '0' + Month
    }
    return `${Year}年${Month}月${Day}日 ${Hour}时${Minute}分${Second}秒 星期${Week}`
}
time() //载入时间对象 否则为当前时间
```


## 事件

### 事件模型

w3c中定义的事件发生的过程的3个阶段： 捕获阶段（capturing）、目标阶段（targetin）、冒泡阶段（bubbling）

- 捕获阶段 useCapture = true
- 事件目标
- 事件冒泡 useCapture = false

默认情况下，所有的事件处理程序都是在冒泡阶段内注册的，就是是说 `addEventListener` 注册的事件处理的是阶段是冒泡阶段

### e.target 和 e.currenttarget 的区别

e.target 是事件触发的元素，操作的元素

e.currentTarget 是事件绑定的元素

###  常见事件
```
# PC 端
onkeypress  键盘按下时触发事件
onmousedown 鼠标按下时事件
onmouseup   鼠标释放时触发事件
onmousemove 鼠标移动时时间
onmouseenter  鼠标移入（悬停）
onmouseleave  鼠标移出

# 移动端或触屏设备
ontouchstart    手指触摸时触发事件
ontouchend  手指触摸结束时触发事件
ontouchmove 手指移动时触发事件

由于触屏设备支持多点触控，可以通过 touches 属性获取多个点

# 滚动事件

window.scroll(x, y)
window.scroll(0, 100) // 向下滚动 100px

# 监听页面滚动事件
window.onscroll = function(xxx){
    
}

window.scrollY // 获取文档滚动过的Y轴距离

```

获取页面视口（浏览器窗口）的高度和宽度

```
-- 视口的宽高
document.documentElement.clientWidth
document.documentElement.clientHeight
-- 网页的总宽高
document.body.clientWidth
document.body.clientHeight
```

获取元素在文档的位置

```
获取 DOM 元素相对于文档的位置，可以直接使用 element.offsetTop；
获取 DOM 元素相对于视口的位置，可以使用 .getBoundingClientRect()
获取 SVG 元素或行内元素的 CSS 盒子（比如用来做文本高亮时），可以使用 .getClientRects()；
获取绝对定位元素、伪元素的渲染后 CSS 属性，可以使用 .getComputedStyle()
```

## AJAX

```javascript
window.ajax = function ({ url, method, body, headers }) {
  return new Promise((resolve, reject) => {
    let xhr = new XMLHttpRequest()
    xhr.open(method, url)
    for (const key in headers) {
      if (headers.hasOwnProperty(key)) {
        const value = headers[key];
        xhr.setRequestHeader(key, value)
      }
    }
    xhr.onreadystatechange = function () {
      if (xhr.readyState === 4) {
        if (xhr.status === 200) {
          resolve(xhr.responseText)
        } else if (xhr.status >= 400) {
          reject(xhr)
        }
      }
    }
    xhr.onerror = function(){
      reject(xhr)
    }
    xhr.send(body)
  })
}

ajax({
  url: '/xxx',
  method: 'get',
  headers: {
    'content-type': 'application/x-www-form-urlencoded',
    'fuck-brower': true
  }
}).then(
  (r) => {
    console.log(r)
  },
  (e) => {
    console.log(e)
  }
);
```



## Debug

```javascript
const log = console.log.bind(console, '>>>')

const ensure = function(a, b, message) {
    if (JSON.stringify(a) !== JSON.stringify(b)) {
        log('//', message)
        log(`×　`, a)
        log(`√　`, b)
    }
}
//测试 函数返回值 是否等于 结果(手工计算) 否则 报错
//举例：
let sum = function(a, b) {
    return a + b
}
ensure( sum(3, 3) ,5 ,'sum错误' )
```

