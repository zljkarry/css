# CSS



## css基础语法

**选择器+声明语句**

选择器（selector）通常是需要改变样式的 HTML 元素，属性（property）是希望设置的样式属性（style attribute）

```css

/* 选择器 {
     声明
   } */

selector {
    declaration1; /* 声明语句包括 属性名 和 属性值 */
    declaration2; /* property: value */
    /*...*/
    declarationN;
}
```

![语法](https://github.com/zljkarry/css/blob/master/images/grammar.png)

## css高级语法

1. 同时定义多个html元素的样式（选择器分组），用逗号隔开

   ~~~css
   h1,h2,h3,h4,h5,h6 {
        color: green;
     }
   ~~~

2. 子元素从父元素继承属性

   ~~~html
   <!-- html -->
   <p class="father">
       我一定是橙色
       <p class="child">
           我默认是橙色，但如果你单独给我定义了颜色，那么我将使用你重新定义的颜色
       </p>
   </p>
   ~~~

   ~~~css
   /* css */
   .father {
       color: orange;
   }
   .child {
       color: blue;
   }
   ~~~

   

## css选择器

> 很简单，快速讲完，细节下来自己看哦

**通配选择符  “*”**

~~~css
*{
    margin: 0;
    padding: 0;
    
}
~~~



### 元素选择器/类型选择器

~~~css
html {
   color:black;
}
p {
  color:gray;
}
h2 {
   color:silver;
}
~~~



### 类选择器

给元素归类，通过类名选择元素

**一个元素可以有多个类名，一个类名可由多个元素共享**

本质就是给元素起的别名，可理解为绰号

~~~html
<!-- 基础使用 -->
<div class="class_name">
    <p>
        这是只有类名为cn1的元素内部，我的背景应该是橙色
    </p>
</div>

<div class="cn1">
    <p>
        这是类名只有cn1的元素内部
    </p>
</div>

<!-- 给一个元素添加多个类名 -->
<div class="cn1 cn2">
    <p>
        这是类名同时包含cn1和cn2的元素内部，我的背景应该是红色
    </p>
</div>
~~~

~~~css
/* 基础类选择器 */
.class_name {
    width: 100px;
    height: 100px;
    background-color: orange;
}
.cn1 {
    width: 300px;
    height: 300px;
}

/* 多类选择器 */
.cn1.cn2 {
    background-color: red;
}

~~~

**结合元素选择器**

> 本质和多类选择器一样，将多个选择中间不留空格的连接起来，就会选择同时满足这些选择器的元素

~~~html
<p>
    我是一个无名的p标签
</p>
<p class="blue">
    我是名为blue的p标签，我应该是蓝色
</p>
<div class="blue">
    我是名为blue的div标签
</div>
~~~

~~~css
p.blue {
    background-color: blue;
}
~~~



### ID选择器

给元素一个唯一标识，通过这个唯一标识选择元素

**元素与id一一对应**

本质就是元素独有的，可理解为身份证号

~~~html
<div id="user">
    我是id为user的元素
</div>
~~~

~~~css
#user {
    font-size: 22px;
    color: blue;
}
~~~



### 属性选择器

~~~html
<h2 title="Hello world">
    Hello world
</h2>
<a title="百度" href="https://www.baidu.com/">
   百度
</a>
~~~

**简单属性选择**

如果希望选择有某个属性的元素，而不论属性值是什么，可以使用简单属性选择器。

~~~css
[title] {
  color: red;
}
/* 同上，连接多个选择器即可选择同时满足条件的 */
a[title][href] {
  font-size: 22px;
}
~~~

**根据具体属性值选择**

除了选择拥有某些属性的元素，还可以进一步缩小选择范围，只选择有特定属性值的元素。

~~~css
[title="Hello world"] {
    color: black;
}
~~~



### 后代（包含）选择器

~~~html
<div class="cn1">
    <p class="cn2">
        这是cn1下cn2的元素内部，我的背景色应该是绿色
    </p>
</div>
<div class="cn2">
    这是外层无cn1的cn2的元素内部
</div>
~~~

~~~css
/* cn1下所有cn2 */
.cn1 .cn2 {
    width: 300px;
    height: 300px;
    background-color: green;
}
~~~

**注意：两个元素之间的层次间隔可以是无限的**

~~~html
<ul>
  <li>List item 1
    <ol>
      <li><em>List item 1-1</em></li>
      <li>List item 1-2</li>
      <li>List item 1-3
        <ol>
          <li>List item 1-3-1</li>
          <li>List item <em>1-3-2</em></li>
          <li>List item 1-3-3</li>
        </ol>
      </li>
      <li>List item 1-4</li>
    </ol>
  </li>
  <li>List item 2</li>
  <li>List item 3</li>
</ul>
~~~

~~~css
ul li {
  font-size: 22px;
}
ul em {
  color: blue;
}
~~~



### 子元素选择器

**不希望选择任意的后代元素，可以只选择子元素**

~~~css
/* ">"号左右可有空格，也可无空格 */
ul>li {
  color: red;
}
~~~



### 相邻兄弟选择器

**可选择紧接在另一元素后的元素，且二者有相同父元素**

~~~css
/* "+"号左右可有空格，也可无空格 */

/* 选择了紧接着h1后面的p元素 */
h1 + p {
    margin-top:50px;
}

/* 选择了紧接着li后面的li元素 */
li + li {
    font-weight:bold;
}
~~~



### 伪类

**给既存的元素模拟新添加一个类来实现某种效果**

* :link

* :visited

* :hover

* :active
* :first-child



### 伪元素

**模拟新添加一个元素来实现某种效果**

* ::before

* ::after



*伪类和伪元素具体的暂时就先不讲了，可参考W3school和菜鸟教程等*

推荐文章：[CSS伪类伪元素详解](https://segmentfault.com/a/1190000006701056)



## 选择器权重

> 比较复杂，了解常用的，复杂的用到的时候再查就行

**标签的权值为1，类选择符的权值为10，ID选择符的权值最高为100。**例如下面的代码：

```css
p{color:red;} /*权值为1*/
p span{color:green;} /*权值为1+1=2*/
.warning{color:white;} /*权值为10*/
p span.warning{color:purple;} /*权值为1+1+10=12*/
#footer .note p{color:yellow;} /*权值为100+10+1=111*/
```

**注意：还有一个权值比较特殊--继承也有权值但很低，有的文献提出它只有0.1，所以可以理解为继承的权值最低。**

有些特殊的情况需要为某些样式设置具有最高权值，使用**!important**

如下代码：

```css
/* 这时 p 段落中的文本会显示的red红色 */
p{color:red!important;}
p{color:green;}
```



## 盒模型

**width、height、padding、border、margin**

* 可用**负值**

* 可用**百分比**，但很不常用

普通元素的百分比是参照其父元素的宽度，绝对定位的元素参照第一个定位祖先(absolute,relative,fixed)的宽度

### **margin塌陷和合并问题**

**塌陷**

~~~html
<div class="warpper">
    <div class="content">
        
    </div>
</div>
~~~

~~~css
.wrapper {
    width: 300px;
    height: 300px;
    margin-top: 100px;
}
.content {
    width: 100px;
    height: 100px;
    margin-top: 50px;
    /* margin-top: 150px; */
}
~~~

**合并**

~~~html
<div class="box1"></div>
<div class="box2"></div>
~~~

~~~css
.box1 {
    width: 300px;
    height: 300px;
    margin-bottom: 100px;
    background-color: red;
}
.box2 {
    width: 300px;
    height: 300px;
    margin-top: 100px;
    background-color: blue;
}
~~~

**解决**

这会涉及到BFC（block format context——块级格式化上下文），有兴趣的可以看看



### W3C的标准盒模型

> box-sizing: content-box

元素实际大小=width/height+padding+border+margin

![标准盒模型](https://github.com/zljkarry/css/blob/master/images/standard.png)



### IE盒模型

> box-sizing: border-box

元素实际大小=width/height+margin

![IE盒模型](https://github.com/zljkarry/css/blob/master/images/ie.png)



### 盒模型切换

box-sizing: content-box/border-box; 视情况使用哪种盒模型



## 布局

[深入浅出CSS布局](http://layout.imweb.io/)

### 文档流

**文档流**指的是元素排版布局过程中，元素会**默认**自动从左往右，从上往下的**流式排列方式**

### display

* block                块级元素
* inline                行内元素 / 内联元素
* inline-block      行内块级元素
* none                  隐藏元素
* flex                    flex布局
* grid                    grid布局

### float

[CSS深入理解之float浮动](https://segmentfault.com/a/1190000014554601)

### position

* static                默认值，正常位置
* relative            相对定位，相对于其正常位置进行定位
* absolute          绝对定位，相对于 static 定位以外的第一个父元素进行定位，若没有则相对于html
* fixed                 固定定位，相对于浏览器窗口进行定位
* sticky

**top/bottom/left/right**

1. **值**

`bottom:-20px;`向下移动

`left:50px;`向右移动

* 可为**负值**，表示向相反的方向移动

* 可为**百分比**，水平偏移量根据其父元素 width 属性的值计算得到，垂直偏移量根据其父元素 height 属性的值计算得到，但如果父元素没有显式定义 height 属性，就等同于 height 属性的值为 0

2. **表现**

* 绝对或固定元素会生成一个块级框，而不论该元素本身是什么类型

* 固定元素不占据空间，即使窗口滚动它也不会滚动

* 相对定位元素仍然占据文档中的原有位置，并且对父元素和兄弟元素的布局都没有任何影响，但可能会覆盖其他元素

* relative和fixed脱离文档流，子元素无法撑起父元素的高度

3. **z-index**

> 只能在position属性值为relative或absolute或fixed的元素上有效

三维坐标系的z轴，简单来说值越大，越在最上层

友链：[深入理解css中position属性及z-index属性](https://www.cnblogs.com/zhuzhenwei918/p/6112034.html)

### flex

Flexible Box，弹性盒子

[青蛙小游戏](https://flexboxfroggy.com/#zh-cn)

[Flex深入浅出](http://layout.imweb.io/article/flexbox.html)

**Flex Container（父级）的属性**

* display：flex
* flex-direction
* flex-wrap
* flex-flow
* justify-content
* align-items
* align-content

**Flex Item 的属性**

* align-self
* order
* flex-flow
* flex-shrink
* flex-basis

### Grid

网格布局（兼容性不是很好）

[花园小游戏](https://cssgridgarden.com/#zh-cn)

[Grid深入浅出](http://layout.imweb.io/article/grids.html)

**Grid Container（父级）的属性**

* display
* grid-template-rows
* grid-template-columns
* grid-gap
* grid-template-areas
* grid-auto-rows
* grid-auto-columns
* grid-auto-flow
* justify-items
* align-items
* justify-content
* align-content

**Grid Item 的属性**

* grid-column
* grid-row
* grid-area
* justify-self
* align-self



### 居中方案

*定宽高的当然也可以用不定宽高的居中方案*

**水平**

- **非绝对定位定宽块级**元素水平居中

- **内联元素**水平居中 在外层用 text-align:center

- **定宽块级**元素水平居中

  - 非绝对定位加margin-left和margin-right设为auto
  - 绝对定位left: 50%; 加 margin-left: -50px; (假设宽度100px)

- **任意块级**元素水平居中

  - 绝对定位left: 50%; 加 transform: translateX(-50%); 
  
  - 绝对定位加margin: auto
  
    绝对定位left: 0; right: 0; 加 margin-left 和 margin-right 设置为 auto
  
  - **inline-block（可多个）**
  
    父元素text-align: center: 子元素display: inline-block;
  
  - **flex布局（可多个）**
  
    父元素设置display: flex; justify-content: center; align-items: center;

**垂直**

- **单行文字**垂直居中

  * 将line-height设为与父元素高度相同
  * padding上下填充相同

- **多行文本**垂直居中

  * padding填充上下相同

  * flex布局，外层元素定高加以下代码，（会将内部子元素变成block类型）

    ```css
    display: flex;
    flex-direction: column;
    justify-content: center;
    ```

- **定高块级**元素垂直居中

  子元素绝对定位 top: 50%; 和负边距 margin-top: -50px; (假设宽度100px)

- **不定高块级**元素垂直居中

  * 子元素绝对定位 top: 50%; 加transform: translateY(-50%);

  - 绝对定位加margin: auto;

    设置元素为绝对定位且top与bottom均为零，margin-top与margin-bottom为auto

  - flex布局

  ```css
  /* 会将居中元素内的文本也垂直居中 */
  .wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  ```

**水平垂直**

- **定宽定高**

  绝对定位加负边距

- **不定宽高**

  * 绝对定位left: 50%; top: 50%; 加 transform: translate(-50%,-50%);

  - 绝对定位加margin: auto;

    设置元素为绝对定位且top、bottom、left与right均为零，margin值为auto

  - flex布局

    父元素设置display: flex; justify-content: center; align-items: center;

  - Grid布局

    父元素display: grid; 子元素设置justify-self: center; align-self: center; 



## css&css3

- opacity (0~1的数)

- overflow

  - hidden
  - scroll
  - auto

- color

  - 颜色名
  - 十六进制  #000 #fff #ff0000
  - rgb(red, green, blue) 百分比或0~255整数
  - rgba(red, green, blue, alpha)

- 框模型

  box-sizing: content-box/border-box

- 背景 background

  * background-color
  * background-image
  * background-repeat
  * background-position
  * background-size
  * background-origin

- 边框 border

  - border-radius
  - box-shadow
  - border-image

- 文本效果

  * color
  * text-indent
  * text-align
  * line-height
  * word-spacing 字间隔
  * letter-spacing 字母间隔
  * text-transform
  * text-decoration
  * direction

  - text-shadow
  - word-wrap

- 2D 转换 transform

  - translate()
  - rotate()
  - scale()
  - skew()
  - matrix()

- 3D 转换 transform

  - rotateX()
  - rotateY()

- 过渡 transition

  > transition--duration

- 动画 animation

  > 自定义动画@keyframes + animation-name { }
  >
  > animation: animation-name, animation-duration



## css样式层叠

**CSS 指层叠样式表 (*C*ascading *S*tyle *S*heets)**

样式表允许以多种方式规定样式信息。样式可以规定在单个的 HTML 元素中，在 HTML 页的头元素中，或在一个外部的 CSS 文件中。甚至可以在同一个 HTML 文档内部引用多个外部样式表。

**层叠次序**

> 多重样式将层叠为一个

*某个HTML元素的同一个属性在不同地方定义时，这个属性采用哪里定义的值的问题*

1. 浏览器缺省设置

2. 外联：`<link rel="stylesheet" href="./demo.css">`

3. 内联：`<div style="bcakground-color: red">`

4. 内嵌：`<head><style></style></head>`

在选择器权重一样的情况下，1,2,3,4的优先权依次升高，即优先级遵守就近原则。

**以后都要求使用外联css文件**



## 关于一些规范问题

> 让自己的逻辑更清晰，让别人更快更好的看懂你的代码

**我接下来说的很重要很重要很重要！！！**

### 命名

**不管是文件名，还是class或id名，都不要用中文**

**class或id命名最好按语义来，两个及以上的单词用下划线连接**

常见：

外套 wrap/wrapper -------------用于外层

头部 header ----------------用于头部

容器 container --------------用于外层

主要内容 main ------------用于主体内容（中部）

左侧 main_left -------------左侧布局

右侧 main_right -----------右侧布局

导航条 nav -----------------网页菜单导航条

列表 list -----------------用于多个同类元素的外层

内容 content ---------------用于网页中部主体

底部 footer -----------------用于底部

### 文件目录结构



### 一些小点

> 请逐条检查自己是不是做好了

1. 下载谷歌浏览器，并把谷歌浏览器设为默认浏览器
2. 有一个专属红岩作业的文件夹，每一项作业放在一个文件夹中

3. 文件包括图片命名用英文
4. 文件显示后缀名

**有时间建议做笔记和总结**

做笔记的推荐有余力的同学学一下Markdown语法，使用Typora



## 使用GitHub

安装git

https://git-scm.com/downloads

注册GitHub

https://github.com/

使用



## 作业

* level1: 登陆弹窗 （即完成上周的进阶作业）

* level2: [豆瓣](https://www.douban.com/)官网

  > 必须包含导航栏、banner（包括登陆框）、版尾；中间的热门内容，豆瓣时间，视频，电影，小组，读书，音乐，豆品，同城，这几个板块可选

* level3: lv2中选择一个板块
* level4: lv2中选择两个板块
* 依次类推
* ···

**导航栏和版尾在写百度首页时已经写过了，登陆框level1从上周就开始写了，所以其实不难**

**要求：**

1. **布局方法不做限制，希望你们能灵活运用所学，不过不能太单一。**

2. **至少完成level1，level2**

3. **将你GitHub上的仓库地址（注明登陆弹窗和豆瓣官网）发到邮箱zhaolijia@redrock.team**

4. **邮件主题格式示例：lv3王凯利2019210002**

   > 示例信息纯属虚构哈

5. **请在第八周周五23：59之前交作业**



## 学习资源

[GitHub](<https://github.com/>)

### 在线文档

- [MDN](<https://developer.mozilla.org/zh-CN>)
- [W3C](<http://www.chinaw3c.org/>)
- [w3school](<http://www.w3school.com.cn/>)
- [w3cschool](https://www.w3cschool.cn/index.html)
- [菜鸟教程](<http://www.runoob.com/>)
- [廖雪峰官方网站](https://www.liaoxuefeng.com/)

### 技术论坛

- [CSDN](<https://www.csdn.net/>)
- [掘金](<https://juejin.im/>)
- [SegmentFault思否](<https://segmentfault.com/>)

### 视频教程

- [哔哩哔哩](https://www.bilibili.com/)
- [慕课网](<https://www.imooc.com/>)
- [腾讯课堂](<https://ke.qq.com/>)
- [网易云课堂](<https://study.163.com/>)