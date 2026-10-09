# HTML / CSS 学习笔记

[学习笔记总目录](../README.md) · [前端专区](README.md) · [算法专区](../algorithms/README.md)

> **当前进度**：已整理 HTML 基础；CSS 章节待后续补充。
> 本文保留原笔记的讲解和代码示例，统一章节层级，并修正部分易错表述。
> 课件中的 `marquee`、`bgcolor`、表格表现属性和 `frameborder` 等旧写法用于理解历史示例，新项目优先采用现代 HTML 与 CSS。

## 学习地图

| 模块 | 学习内容 | 入口 |
| --- | --- | --- |
| 1 | 网页与 HTML 入门 | [开始阅读](#module-1) |
| 2 | 文本与页面结构 | [开始阅读](#module-2) |
| 3 | 图片与资源路径 | [开始阅读](#module-3) |
| 4 | 超链接与导航 | [开始阅读](#module-4) |
| 5 | 列表、表格与补充标签 | [开始阅读](#module-5) |
| 6 | 表单与嵌入内容 | [开始阅读](#module-6) |
| 7 | 字符、全局属性与元信息 | [开始阅读](#module-7) |
| 8 | CSS 基础（待补充） | [查看学习路线](#css-roadmap) |

<details>
<summary>展开完整知识点目录</summary>

**1. 网页与 HTML 入门**

- [应用软件的两种架构](#topic-1-1)
- [HTML 标签](#topic-1-2)
- [浏览器怎么渲染](#topic-1-3)
- [标签上的属性](#topic-1-4)
- [HTML 的注释](#topic-1-5)
- [一个 HTML 页面的开头](#topic-1-6)

**2. 文本与页面结构**

- [h 标签](#topic-2-1)
- [p 标签](#topic-2-2)
- [div 标签](#topic-2-3)
- [语义化标签](#topic-2-4)
- [块级元素和行内元素](#topic-2-5)
- [元素的嵌套规则](#topic-2-6)
- [文本标签](#topic-2-7)

**3. 图片与资源路径**

- [图片标签](#topic-3-1)
- [常见图片格式](#topic-3-2)

**4. 超链接与导航**

- [超链接](#topic-4-1)

**5. 列表、表格与补充标签**

- [列表](#topic-5-1)
- [表格](#topic-5-2)
- [常用标签补充](#topic-5-3)

**6. 表单与嵌入内容**

- [表单](#topic-6-1)
- [框架标签](#topic-6-2)

**7. 字符、全局属性与元信息**

- [常见字符实体](#topic-7-1)
- [HTML 全局属性](#topic-7-2)
- [meta 元信息](#topic-7-3)

</details>

---

<a id="module-1"></a>

## 1. 网页与 HTML 入门

> **学习目标**：理解网页组成、标签、属性、注释和页面骨架。

<a id="topic-1-1"></a>

### 1.1 应用软件的两种架构

应用软件按用户怎么访问，分成两条路：装客户端，或打开浏览器。

```text
应用软件
├── C/S 架构：Client / Server，客户端 / 服务器
└── B/S 架构：Browser / Server，浏览器 / 服务器
```

| 缩写 | 英文 | 含义 |
| --- | --- | --- |
| C | Client | 客户端 |
| B | Browser | 浏览器 |
| S | Server | 服务器 |

**C/S 架构**

用户先安装专门的客户端，客户端再和服务器通信。

特点：

- 界面和功能做在客户端里，体验可以更完整，也能用到本机能力。
- 换电脑或换版本，通常要重新安装或更新客户端。
- 开发要同时维护客户端和服务器。

**B/S 架构**

用户不装专用客户端，用浏览器打开网址，页面从服务器取回来再显示。

课件下方的几张图，都是在浏览器窗口里打开的网页。

特点：

- 浏览器就是统一的“客户端”。
- 改页面主要改服务器上的文件，用户刷新就能看到新版本。
- 页面本身由 HTML、CSS、JavaScript 组成。HTML 管结构，CSS 管样子，JavaScript 管交互。

| 网页组成 | 技术 | 负责什么 |
| --- | --- | --- |
| 结构 | HTML | 内容与语义 |
| 表现 | CSS | 样式与布局 |
| 行为 | JavaScript | 交互与逻辑 |

**HTML**：超文本标记语言（HyperText Markup Language）。

<a id="topic-1-2"></a>

### 1.2 HTML 标签

1. 标签又称元素，是 HTML 的基本组成单位。
2. 标签分为双标签与单标签，绝大多数都是双标签。
3. 标签名不区分大小写，但推荐小写，因为小写更规范。
4. 双标签：

```html
<标签名>标签体</标签名>
```

- `<标签名>` 是起始标签
- 中间是标签体
- `</标签名>` 是结束标签

示例：

```html
<marquee>尚硅谷，让天下没有难学的技术！</marquee>
```

5. 单标签（空元素）：不包含标签体，不写结束标签，例如 `<br>`、`<img>`、`<input>`。

<a id="topic-1-3"></a>

### 1.3 浏览器怎么渲染

浏览器解析 HTML 并构建 DOM，再结合 CSS 进行布局和绘制；解析过程中会按 HTML 的错误处理规则修复部分不规范的结构。

- HTML 结构正确：通常更容易得到预期的 DOM。
- HTML 结构错误：浏览器可能隐式闭合或补出节点，显示结果不一定符合意图。

> **易错**：页面能显示不代表 HTML 写法正确。

只写一行 `<marquee>尚硅谷</marquee>` 时，浏览器会补成完整页面：

```html
<html>
  <head></head>
  <body>
    <marquee>尚硅谷</marquee>
  </body>
</html>
```

`<head>` 放标题、样式这些不直接显示的内容，`<body>` 放页面上能看到的内容。

<a id="topic-1-4"></a>

### 1.4 标签上的属性

属性写在起始标签里，用来补充这个标签的设置。格式是：

```html
<标签名 属性名="属性值">
```

一个标签可以写多个属性，属性之间用空格分开。属性值建议加双引号。

#### bgcolor

`bgcolor` 设置背景颜色。颜色可以写颜色名，也可以写十六进制。

```html
<body bgcolor="pink"></body>
<marquee bgcolor="yellow">尚硅谷，让天下没有难学的技术！</marquee>
```

现在新页面更常用 CSS 的 `background-color`。课件里仍用 `bgcolor` 演示属性怎么写。

#### marquee

`marquee` 是滚动字幕标签，不是属性。文字会在页面上滚动。上面的 `bgcolor` 可以写在它的起始标签上。

```html
<marquee bgcolor="pink" direction="left" behavior="scroll">
  尚硅谷，让天下没有难学的技术！
</marquee>
```

常用属性：

| 属性 | 作用 | 常见值 |
| --- | --- | --- |
| bgcolor | 背景颜色 | `pink`、`yellow`、`#ff0000` |
| direction | 滚动方向 | `left`、`right`、`up`、`down` |
| behavior | 滚动方式 | `scroll` 循环滚、`slide` 滚到头停下、`alternate` 来回滚 |
| loop | 滚动次数 | 数字；不写则一直滚 |
| scrollamount | 每次滚动的距离 | 数字，越大越快 |

`marquee` 是旧标签，新页面里的滚动效果改用 CSS。这里按课件先记住写法。

#### disabled

`disabled` 表示禁用。加上之后，这个控件看得见，但不能输入、也不能点击。它通常不用写属性值。

```html
<input type="text" disabled>
<input type="password" disabled>
<button disabled>不能点</button>
```

去掉 `disabled`，控件恢复可用。

#### type="password"

`type` 规定输入框的类型，写在 `<input>` 上。

```html
<input type="text">
<input type="password">
```

- `type="text"`：普通文本框，输入什么就显示什么。
- `type="password"`：密码框，输入的字符显示成圆点，避免旁人直接看到密码。

`<input>` 上还会碰到这些 `type`：

| type | 画面上是什么 |
| --- | --- |
| text | 单行文本框 |
| password | 密码框 |
| radio | 单选按钮，同一组里只能选一个 |
| checkbox | 复选框，可以选多个 |
| button | 普通按钮 |
| submit | 提交按钮 |
| reset | 重置按钮，将控件恢复到初始值 |
| file | 选择文件 |

<a id="topic-1-5"></a>

### 1.5 HTML 的注释

注释写给看代码的人，浏览器不显示，页面上看不到。

```html
<!-- 这是一行注释 -->

<!--
  也可以写成多行。
  浏览器同样不会显示。
-->
```

用来说明这段代码是干什么的，或者临时停掉一段代码：

```html
<!-- <marquee bgcolor="pink">这段先不显示</marquee> -->
```

写法记住三点：

- 以 `<!--` 开头，以 `-->` 结尾。
- 注释里面不要再套一层 `<!-- -->`。
- 编辑器里常用 `Ctrl + /` 给当前行加上或去掉注释。

CSS 的注释是另一套写法：`/* 注释内容 */`。HTML 文件里的说明用 `<!-- -->`。

<a id="topic-1-6"></a>

### 1.6 一个 HTML 页面的开头

浏览器打开页面时，先看这几行：这是什么文档、用哪种文字编码、页面是哪种语言、标签页上用哪张小图标。

```html
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="UTF-8">
    <title>页面标题</title>
    <link rel="icon" href="favicon.ico">
  </head>
  <body>
  </body>
</html>
```

#### DOCTYPE 文档声明

`<!DOCTYPE html>` 写在文件第一行，告诉浏览器：按 HTML5 来解析这个页面。

- 它是声明，不是标签，所以没有结束标记。
- 不区分大小写，习惯写成 `<!DOCTYPE html>`。
- 漏写时，浏览器可能用旧的兼容模式排版，页面容易和预期不一致。

#### meta charset

`<meta charset="UTF-8">` 写在 `<head>` 里，规定页面文字用 UTF-8 编码。

- UTF-8 能同时保存中文、英文和常见符号。
- 文件本身也要存成 UTF-8。声明和文件编码不一致时，中文会变成乱码。
- 它是单标签，没有 `</meta>`。

#### html lang

`<html lang="zh-CN">` 说明这份页面的主要语言是简体中文。

- `lang` 是 `<html>` 的属性。`zh-CN` 是简体中文，`en` 是英文。
- 读屏软件按这个语言来朗读。
- 搜索引擎也能据此判断页面语言。

#### 配置 .ico 图标

`.ico` 是标签页上那个小图标，也叫 favicon。把图标文件放进网站目录，再在 `<head>` 里写：

```html
<link rel="icon" href="favicon.ico">
```

- `rel="icon"` 表示这是网站图标。
- `href` 写图标文件的路径。文件名常叫 `favicon.ico`，也可以用 `.png`。
- 改完后如果标签页没变，多半是浏览器还记着旧图标，强制刷新或清缓存后再看。

#### MDN 开发者文档

查标签、属性怎么写，用 MDN：<https://developer.mozilla.org/zh-CN/>

- 每个标签有一篇说明：作用、可用属性、示例、浏览器是否支持。
- 地址栏搜 `MDN` 加标签名，例如 `MDN h1`、`MDN meta charset`。
- 课件里的旧写法（如 `bgcolor`、`marquee`）在 MDN 上会标成已过时。写新页面时以 MDN 为准。

<a id="module-2"></a>

## 2. 文本与页面结构

> **学习目标**：掌握标题、段落、语义化、元素显示方式与嵌套规则。

<a id="topic-2-1"></a>

### 2.1 h 标签

`<h1>` 到 `<h6>` 是标题，数字越小级别越高。`<h1>` 是全页最重要的标题，一个页面通常只有一个。

```html
<h1>尚硅谷</h1>
<h2>HTML</h2>
<h3>标题标签</h3>
```

- 浏览器会把它们显示成由大到小的粗体，并自带上下间距。
- 标题表达的是层级，不是为了把字变大。想调大小用 CSS。
- 不要跳级硬凑，例如 `<h1>` 下面直接用 `<h4>`。

<a id="topic-2-2"></a>

### 2.2 p 标签

`<p>` 表示一段正文。

```html
<p>尚硅谷，让天下没有难学的技术！</p>
<p>这是第二段。</p>
```

- 每一段独占一块，段与段之间有空隙。
- 段落里按回车不会在页面上换行。要换行用 `<br>`。
- 一段一个意思。不要把整页正文都塞进同一个 `<p>`。

<a id="topic-2-3"></a>

### 2.3 div 标签

`<div>` 是一个通用盒子，用来把若干标签包成一组，方便排版。

```html
<div>
  <h2>HTML</h2>
  <p>超文本标记语言。</p>
</div>
```

- 它本身没有专门含义，页面上默认看不出盒子边界。
- 需要统一设置背景、宽度、间距时，先用 `<div>` 包起来，再写 CSS。
- 能用更明确的语义化标签时，就不要一律用 `<div>`。

<a id="topic-2-4"></a>

### 2.4 语义化标签

语义就是含义。标签带不带语义，看它的名字能不能说明这块内容是什么。

| 标签 | 有没有语义 | 含义 |
| --- | --- | --- |
| h1–h6 | 有 | 标题 |
| p | 有 | 段落 |
| div | 没有 | 只是一个盒子，不说明里面是什么 |

语义化：标签默认的效果不重要，语义最重要。

`<h1>` 默认又大又粗，`<p>` 默认有段间距，这些外观都可以用 CSS 改掉。选标签时先看含义对不对，不要为了字大就用 `<h1>`，也不要因为 `<div>` 没有默认样式就拿它代替标题和段落。

好处：

1. 代码的可读性强、清晰。看到标签名就知道这块是标题、段落还是普通分组。
2. 有利于 SEO（搜索引擎优化）。搜索引擎的爬虫、抓取代码的机器人能分清标题和正文。
3. 方便设备解析。屏幕阅读器、盲人阅读器按语义朗读和跳转，而不是只看到一堆没有含义的盒子。

页面结构上还有这些带语义的标签：

| 标签 | 这块内容是什么 |
| --- | --- |
| header | 页头，常放标题和标志 |
| nav | 导航 |
| main | 页面的主体内容，一页一个 |
| article | 一篇可以单独拿出去的内容，例如文章、帖子 |
| section | 文档里的一个章节 |
| aside | 旁边的附属内容，例如侧栏 |
| footer | 页脚，常放版权、联系方式 |

```html
<header>
  <h1>尚硅谷</h1>
  <nav>首页 HTML CSS</nav>
</header>
<main>
  <article>
    <h2>HTML 标签</h2>
    <p>标签是 HTML 的基本组成单位。</p>
  </article>
</main>
<footer>版权所有</footer>
```

好处和作用：

- 代码好读。看到 `nav`、`footer` 就知道是导航和页脚，比一排 `div` 清楚。
- 读屏软件能按区域跳转，方便视障用户。
- 搜索引擎更容易分清标题、正文和导航，有利于收录。
- 样式和脚本可以按区域来写，以后改页面不容易改错地方。
- `<div>` 仍然有用：纯粹为了布局、又没有合适语义时再用它。

<a id="topic-2-5"></a>

### 2.5 块级元素和行内元素

元素在页面上的占位分两种：自己占一整行，或者跟在别的内容后面、不换行。

#### 块级元素

特点：独占一行。写两个，第二个会跑到下一行，即使这一行后面还有空位。

课件里的例子：

```html
<!-- 块级元素，特点：独占一行 -->
<marquee>尚硅谷</marquee>
<marquee>尚硅谷</marquee>
<h1>尚硅谷</h1>
<h1>尚硅谷</h1>
<p>尚硅谷</p>
<p>尚硅谷</p>
<div>尚硅谷</div>
<div>尚硅谷</div>
```

常见块级元素：`h1`–`h6`、`p`、`div`、`marquee`，以及 `header`、`nav`、`main`、`footer`。

#### 行内元素

特点：不独占一行。几个可以排在同一行，宽度默认只包住自己的内容。

```html
<!-- 行内元素，特点：不独占一行 -->
<input type="text">
<input type="text">
```

两个文本框会并排出现。常见行内元素还有 `span`、`a`、`strong`、`em`。

`<input>` 是单标签，这里用 `type="text"` 显示成普通文本框。

<a id="topic-2-6"></a>

### 2.6 元素的嵌套规则

下面是课件用于入门的简化记法。严格的嵌套规则由元素的内容模型决定，不能只按 CSS 的块级/行内显示方式判断。

> **易错**：修改 `display` 不会改变 HTML 的合法嵌套规则。参考 [MDN：内容分类](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories)。

#### 规则 1

块级元素里能写行内元素，也能写块级元素，几乎什么都能写。

```html
<!-- 规则1: 块级元素中能写：行内元素、块级元素（几乎什么都能写） -->
<div>
  <h2>标题</h2>
  <p>段落</p>
  <input type="text">
</div>
```

`<div>` 是块级元素，里面放了块级的 `h2`、`p`，也放了行内的 `input`。

#### 规则 2

行内元素里能写行内元素，但不能写块级元素。

```html
<!-- 规则2: 行内元素中能写：行内元素，但不能写：块级元素 -->
<span>
  <a href="#">链接</a>
  <input type="text">
</span>
```

`<span>` 里可以再放 `<a>`、`<input>`。不要在里面写 `<div>`、`<p>`、`<h1>` 这类块级元素。

#### 特殊规则

这两条比上面的总规则更严，即使外层是块级元素也不行。

`h1`–`h6` 不能互相嵌套。标题只能上下并列，不能一个标题套住另一个标题。

```html
<!-- 特殊规则：h1-h6不能互相嵌套 -->
<h1>一级标题</h1>
<h2>二级标题</h2>

<!-- 错误：标题里面再套标题 -->
<h1>
  <h2>不能这样写</h2>
</h1>
```

`p` 标签里不能写块级元素。段落里可以写文字和行内元素，不能写 `div`、`h1`、另一个 `p`。

```html
<!-- 特殊规则：p标签中不能写块元素 -->
<p>段落里可以有 <a href="#">链接</a></p>

<!-- 错误：p 里面放了 div -->
<p>
  <div>不能这样写</div>
</p>
```

写错时，浏览器会按前面的格式检查把结构拆开再渲染，页面结构就和源码对不上了。

<a id="topic-2-7"></a>

### 2.7 文本标签

文本标签用来包裹词汇、短语。它们通常写在排版标签里面。

- 排版标签更宏观，管大段文字，例如 `h1`–`h6`、`p`、`div`。
- 文本标签更微观，管词汇、短语。
- 文本标签通常都是行内元素。

#### 常用的

| 标签名 | 标签语义 | 单/双标签 |
| --- | --- | --- |
| em | 要着重阅读的内容 | 双 |
| strong | 十分重要的内容，语气比 em 更强 | 双 |
| span | 没有语义，用来包裹短语的通用容器 | 双 |

```html
<p>这是<em>要着重读</em>的一句，这是<strong>十分重要</strong>的一句。</p>
<p>用<span>没有语义的 span</span>包住几个字，方便以后单独设样式。</p>
```

#### 不常用的

编码时不用过于纠结，酌情使用，不用也没毛病。

| 标签名 | 标签语义 | 单/双标签 |
| --- | --- | --- |
| cite | 作品标题：书籍、歌曲、电影、电视节目、绘画、雕塑 | 双 |
| dfn | 特殊术语，或专属名词 | 双 |
| del 与 ins | del 是删除的文本，ins 是插入的文本 | 双 |
| sub 与 sup | sub 是下标文字，sup 是上标文字 | 双 |
| code | 一段代码 | 双 |
| samp | 从正常上下文里提取出来的内容，例如设备输出 | 双 |
| kbd | 键盘文本，表示这段文字是用键盘输入的，常见于计算机手册 | 双 |
| abbr | 缩写，最好配上 title 属性 | 双 |
| bdo | 更改文本方向，配合 dir 属性。可选 ltr（默认，从左到右）、rtl（从右到左） | 双 |
| var | 标记变量，可以和 code 一起用 | 双 |
| small | 附属细则，例如版权、法律文本。很少使用 | 双 |
| b | 摘要中的关键字、评论中的产品名称。很少使用 | 双 |

```html
<p><cite>HTML 教程</cite>里把 <dfn>语义化</dfn> 定义成：标签要表达含义。</p>
<p>原价<del>100</del>，现价<ins>80</ins>。水的化学式是 H<sub>2</sub>O，平方写成 x<sup>2</sup>。</p>
<p>按 <kbd>Ctrl</kbd> + <kbd>S</kbd> 保存。变量 <var>x</var> 写在 <code>let x = 1</code> 里。</p>
<p><abbr title="超文本标记语言">HTML</abbr> 是缩写，鼠标停上去能看到 title。</p>
<p><bdo dir="rtl">这段从右往左排</bdo></p>
```

备注：

1. 这些不常用的文本标签，酌情使用即可。
2. `blockquote` 和 `address` 默认以块级方式显示；本节其他示例标签通常以行内方式显示，外观可由 CSS 调整。
3. `small`、`b`、`u`、`q`、`blockquote` 也有各自的语义，应按内容选择，不能仅凭默认外观判断。
4. HTML 标签太多。先记住重要的、语义感强的：`h1`–`h6`、`p`、`div`、`em`、`strong`、`span`。

<a id="module-3"></a>

## 3. 图片与资源路径

> **学习目标**：认识图片属性、相对路径与图片格式。

<a id="topic-3-1"></a>

### 3.1 图片标签

#### 基本使用

`<img>` 表示图片，是单标签。

| 属性 | 作用 |
| --- | --- |
| src | 图片路径，也叫图片地址，指向图片的具体位置 |
| alt | 图片描述 |
| width | 图片宽度，单位为像素，HTML 属性值写无单位整数，例如 `200` |
| height | 图片高度，单位为像素，HTML 属性值写无单位整数，例如 `200` |

```html
<img src="logo.png" alt="尚硅谷标志" width="200">
```

总结：

1. 像素（`px`）是一种单位，学到 CSS 时再详细讲。
2. 设置宽高时要保持图片原始比例。也可以同时提供符合比例的 `width`、`height` 以预留空间，再用 CSS 控制显示尺寸。
3. 目前先把 `img` 当成行内元素。学到 CSS 时会认识新的元素分类，现在只区分块级和行内。
4. `alt` 的作用：
   - `alt` 为图片提供替代文本，帮助无法看到图片的用户理解内容，也可为搜索引擎提供信息。
   - 图片无法显示时，有些浏览器会把 `alt` 的文字显示出来。
   - 盲人阅读器会朗读 `alt` 的值。

`src` 里写的就是路径。路径分相对路径和绝对路径。

#### 相对路径

相对路径从当前这个 HTML 文件所在的位置出发去找图片。

```html
<!-- 相对路径 -->
<!-- 图片和 html 在同一个文件夹 -->
<img src="logo.png" alt="尚硅谷标志">
<img src="./logo.png" alt="尚硅谷标志">

<!-- 图片在下一级文件夹 images 里 -->
<img src="images/logo.png" alt="尚硅谷标志">

<!-- 图片在上一级文件夹里 -->
<img src="../logo.png" alt="尚硅谷标志">
```

- `./` 表示当前目录，可以省略不写，所以 `logo.png` 和 `./logo.png` 一样。
- `images/logo.png` 表示进入当前目录下的 `images` 文件夹再找图片。
- `../` 表示上一级目录。再往上一级就写成 `../../`。
- 相对路径依赖的是当前位置。后期若调整了文件位置，文件中的路径也要修改。

#### 绝对路径

绝对路径以根位置作为参考点去建立路径。分为两类：本地绝对路径、网络绝对路径。

```html
<!-- 绝对路径，分为两类：本地绝对路径、网络绝对路径 -->

<!-- 本地绝对路径，很少使用 -->
<img src="E:/a/b/c/奥特曼.jpg" alt="奥特曼">

<!-- 网络绝对路径 -->
<img src="http://www.atguigu.com/images/index_new/logo.png" alt="尚硅谷标志">
```

注意点：

- 使用本地绝对路径，一旦更换设备，路径处理起来比较麻烦，所以很少使用。
- 使用网络绝对路径确实方便，但要注意：若服务器开启了防盗链，会造成图片引入失败。
- 自己网站里的图片，优先用相对路径。

<a id="topic-3-2"></a>

### 3.2 常见图片格式

#### jpg

扩展名是 `.jpg` 或 `.jpeg`。它是有损压缩格式，会把肉眼不容易观察出来的细节丢弃。

- 主要特点：支持的颜色丰富、占用空间较小。不支持透明背景，不支持动态图。
- 使用场景：对图片细节没有极高要求的场景，例如网站的产品宣传图。网页里很常见。

#### png

扩展名是 `.png`。它是无损压缩格式，能够更高质量地保存图片。

- 主要特点：支持的颜色丰富、占用空间略大、支持透明背景、不支持动态图。
- 使用场景：想让图片有透明背景，或者想更高质量地呈现图片。例如公司 logo、重要配图。

#### bmp

扩展名是 `.bmp`。它不进行压缩，在最大程度上保留图片更多的细节。

- 主要特点：支持的颜色丰富、保留的细节更多、占用空间极大、不支持透明背景、不支持动态图。

#### gif

扩展名是 `.gif`。它仅支持 256 种颜色，色彩呈现不是很完整。

- 主要特点：支持的颜色较少、支持简单透明背景、支持动态图。
- 使用场景：网页中的动态图片。

#### webp

扩展名是 `.webp`。谷歌推出的一种格式，专门用来在网页中呈现图片。

- 主要特点：支持有损/无损压缩、透明和动画，现代主流浏览器已支持；如果目标包含旧浏览器，再按目标环境提供回退方案。
- 使用场景：网页中的各种图片。

#### base64

base64 不是一种图片文件，而是把图片变成一串文本。

1. 本质：一串特殊的文本。要通过浏览器打开，传统看图应用通常无法打开。
2. 原理：把图片进行 base64 编码，形成一串文本。
3. 如何生成：靠一些工具或网站。
4. 如何使用：直接作为 `img` 标签 `src` 属性的值，并且不受文件位置的影响。
5. 使用场景：一些较小的图片，或者需要和网页一起加载的图片。

```html
<img src="data:image/png;base64,一长串编码" alt="小图标">
```

<a id="module-4"></a>

## 4. 超链接与导航

> **学习目标**：学会页面跳转、下载、锚点与应用协议。

<a id="topic-4-1"></a>

### 4.1 超链接

主要作用：从当前页面进行跳转。

`<a>` 是超链接，双标签。

| 属性 | 作用 | 常用值 |
| --- | --- | --- |
| href | 要跳转的具体位置 | 网址、页面路径、文件路径 |
| target | 跳转时如何打开页面 | `_self` 在本页签中打开；`_blank` 在新页签中打开 |

#### 跳转到页面

```html
<!-- 跳转其他网页 -->
<a href="https://www.jd.com/" target="_blank">去京东</a>

<!-- 跳转本地网页 -->
<a href="./10_HTML排版标签.html" target="_self">去看排版标签</a>
```

注意点：

1. 代码中的多个空格、多个回车，都会被浏览器解析成一个空格。
2. `a` 的内容模型是透明的：能否包含某个元素取决于外层上下文，且不能嵌套 `a`、交互式内容或带 `tabindex` 的后代。参考 [MDN：a 元素](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/a)。

想展示多个回车或空格，后面会讲。

#### 跳转到文件

浏览器能直接打开的文件，点击后在浏览器里查看：

```html
<a href="./resource/自拍.jpg">看自拍</a>
<a href="./resource/小电影.mp4">看小电影</a>
<a href="./resource/小姐姐.gif">看小姐姐</a>
<a href="./resource/如何一夜暴富.pdf">点我一夜暴富</a>
```

浏览器不能打开的文件，会自动触发下载：

```html
<a href="./resource/内部资源.zip">内部资源</a>
```

想强制触发下载，使用 `download` 属性，属性值就是下载后的文件名：

```html
<a href="./resource/小电影.mp4" download="电影片段.mp4">下载电影</a>
```

- 注意 1：若浏览器无法打开文件，则会引导用户下载。
- 注意 2：若想强制触发下载，请使用 `download` 属性，属性值即为下载文件的名称。

#### 跳转到锚点

锚点是网页中的一个标记点。使用分两步：先设置锚点，再跳转过去。

第一步：设置锚点。

```html
<!-- 第一种方式：a 标签配合 name 属性 -->
<a name="test1"></a>

<!-- 第二种方式：其他标签配合 id 属性 -->
<h2 id="test2">我是一个位置</h2>
```

注意点：

1. 具有 `href` 属性的 `a` 标签是超链接，具有 `name` 属性的 `a` 标签是锚点。
2. `name` 和 `id` 都区分大小写，且 `id` 最好别是数字开头。

第二步：跳转锚点。`href` 里用 `#` 加上锚点的名字。

```html
<!-- 跳转到 test1 锚点 -->
<a href="#test1">去test1锚点</a>

<!-- 跳到本页面顶部 -->
<a href="#">回到顶部</a>

<!-- 跳转到其他页面锚点 -->
<a href="demo.html#test1">去demo.html页面的test1锚点</a>

<!-- 刷新本页面 -->
<a href="">刷新本页面</a>

<!-- 执行一段 js。如果还不知道执行什么，可以留空，写成 javascript:; -->
<a href="javascript:alert(1);">点我弹窗</a>
```

- `#test1` 跳到本页名叫 `test1` 的锚点。
- 只写 `#`，跳到本页面顶部。
- `demo.html#test1` 先打开另一个页面，再跳到那个页面的锚点。
- `href=""` 会刷新本页面。
- `href="javascript:;"` 表示点了不跳转。课件里的 `javascript:alert(1);` 是点击后执行一段 JavaScript。

#### 唤起指定应用

通过 `a` 标签，可以唤起设备应用程序。

```html
<!-- 唤起设备拨号 -->
<a href="tel:10010">电话联系</a>

<!-- 唤起设备发送邮件 -->
<a href="mailto:10010@qq.com">邮件联系</a>

<!-- 唤起设备发送短信 -->
<a href="sms:10086">短信联系</a>
```

- `tel:` 后面写电话号码，点击后唤起拨号。
- `mailto:` 后面写邮箱地址，点击后唤起发邮件。
- `sms:` 后面写手机号，点击后唤起发短信。

<a id="module-5"></a>

## 5. 列表、表格与补充标签

> **学习目标**：组织有序内容、表格数据和预格式文本。

<a id="topic-5-1"></a>

### 5.1 列表

#### 有序列表

有顺序或侧重顺序的列表。用 `ol` 包住，每一项用 `li`。

```html
<h2>要把大象放冰箱总共分几步</h2>
<ol>
  <li>把冰箱门打开</li>
  <li>把大象放进去</li>
  <li>把冰箱门关上</li>
</ol>
```

#### 无序列表

无顺序或不侧重顺序的列表。用 `ul` 包住，每一项仍用 `li`。

```html
<h2>我想去的几个城市</h2>
<ul>
  <li>成都</li>
  <li>上海</li>
  <li>西安</li>
  <li>武汉</li>
</ul>
```

#### 列表嵌套

列表中的某项内容，又包含一个列表。嵌套时务必把结构写完整：内层列表要放在某一项 `li` 里面，标签要成对闭合。

```html
<h2>我想去的几个城市</h2>
<ul>
  <li>成都</li>
  <li>
    <span>上海</span>
    <ul>
      <li>外滩</li>
      <li>杜莎夫人蜡像馆</li>
      <li>
        <a href="https://www.opg.cn/">东方明珠</a>
      </li>
      <li>迪士尼乐园</li>
    </ul>
  </li>
  <li>西安</li>
  <li>武汉</li>
</ul>
```

#### 自定义列表

自定义列表是一个包含术语名称以及术语描述的列表。

- 一个 `dl` 就是一个自定义列表。
- 一个 `dt` 就是一个术语名称。
- 一个 `dd` 就是术语描述，可以有多个。

```html
<h2>如何高效的学习？</h2>
<dl>
  <dt>做好笔记</dt>
  <dd>笔记是我们以后复习的一个抓手</dd>
  <dd>笔记可以是电子版，也可以是纸质版</dd>
  <dt>多加练习</dt>
  <dd>只有敲出来的代码，才是自己的</dd>
  <dt>别怕出错</dt>
  <dd>错很正常，改正后并记住，就是经验</dd>
</dl>
```

<a id="topic-5-2"></a>

### 5.2 表格

#### 基本结构

一个完整的表格由四部分组成：表格标题、表格头部、表格主体、表格脚注。最外层是 `table`。

| 部分 | 标签 | 课件里的例子 |
| --- | --- | --- |
| 表格 | table | 整张表 |
| 表格标题 | caption | 学生信息 |
| 表格头部 | thead | 姓名、性别、年龄、民族、政治面貌 |
| 表格主体 | tbody | 张三、李四、王五、赵六四行数据 |
| 表格脚注 | tfoot | 共计：4人 |

课件的标签列表里，`tfoot` 也写成表格注脚，和表格脚注是同一部分。

表格涉及到的标签：

| 标签 | 含义 |
| --- | --- |
| table | 表格 |
| caption | 表格标题 |
| thead | 表格头部 |
| tbody | 表格主体 |
| tfoot | 表格注脚 |
| tr | 每一行 |
| th、td | 每一个单元格 |

`th` 和 `td` 的区别：表格头部中用 `th`，表格主体、表格脚注中用 `td`。

```html
<table>
  <caption>学生信息</caption>
  <thead>
    <tr>
      <th>姓名</th>
      <th>性别</th>
      <th>年龄</th>
      <th>民族</th>
      <th>政治面貌</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>张三</td>
      <td>男</td>
      <td>18</td>
      <td>汉族</td>
      <td>团员</td>
    </tr>
    <tr>
      <td>李四</td>
      <td>女</td>
      <td>20</td>
      <td>满族</td>
      <td>群众</td>
    </tr>
    <tr>
      <td>王五</td>
      <td>男</td>
      <td>19</td>
      <td>回族</td>
      <td>党员</td>
    </tr>
    <tr>
      <td>赵六</td>
      <td>女</td>
      <td>21</td>
      <td>壮族</td>
      <td>团员</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>共计：4人</td>
    </tr>
  </tfoot>
</table>
```

一行用一个 `tr` 包起来。头部那一行的每个格子是 `th`，主体和脚注里的每个格子是 `td`。

#### 常用属性

这些标签都是双标签。`tbody`、`tr`、`tfoot` 的常用属性和 `thead` 相同。`th` 的常用属性和 `td` 相同。

`table`：

| 属性 | 作用 |
| --- | --- |
| width | 设置表格宽度 |
| height | 设置表格最小高度，表格最终高度可能比设置的值大 |
| border | 设置表格边框宽度 |
| cellspacing | 设置单元格之间的间距 |

`thead`，以及属性和它相同的 `tbody`、`tr`、`tfoot`：

| 属性 | 作用 | 可选值 |
| --- | --- | --- |
| height | 设置表格头部高度 | |
| align | 设置单元格的水平对齐方式 | `left` 左对齐，`center` 中间对齐，`right` 右对齐 |
| valign | 设置单元格的垂直对齐方式 | `top` 顶部对齐，`middle` 中间对齐，`bottom` 底部对齐 |

`td`，以及属性和它相同的 `th`：

| 属性 | 作用 |
| --- | --- |
| width | 设置单元格的宽度，同列所有单元格全都受影响 |
| height | 设置单元格的高度，同行所有单元格全都受影响 |
| align | 设置单元格的水平对齐方式 |
| valign | 设置单元格的垂直对齐方式 |
| rowspan | 指定要跨的行数 |
| colspan | 指定要跨的列数 |

课件把单元格高度写成了 `heigth`，属性名是 `height`。

```html
<table width="600" height="200" border="1" cellspacing="0">
  <thead align="center" valign="middle">
    <tr>
      <th width="120">姓名</th>
      <th>性别</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>张三</td>
      <td rowspan="2">示例</td>
    </tr>
    <tr>
      <td>李四</td>
    </tr>
  </tbody>
</table>
```

同一列的单元格不要写成不一样的宽度。培养统一的写法，后面自己和同事都好改。

注意点：

1. `<table>` 的 `border` 可以控制表格边框，但 `border` 值的大小并不控制单元格边框的宽度，只能控制表格最外侧边框的宽度。单元格边框后期靠 CSS 控制。
2. 给某个 `th` 或 `td` 设置了宽度之后，它们所在的那一列的宽度就确定了。
3. 给某个 `th` 或 `td` 设置了高度之后，它们所在的那一行的高度就确定了。

#### 跨行跨列

1. `rowspan`：指定要跨的行数。
2. `colspan`：指定要跨的列数。

写在 `th` 或 `td` 上。格子跨出去之后，被盖住的那个位置不要再写一个单元格。

```html
<table border="1">
  <tr>
    <td colspan="2">这一格跨两列</td>
  </tr>
  <tr>
    <td rowspan="2">这一格跨两行</td>
    <td>右上</td>
  </tr>
  <tr>
    <td>右下</td>
  </tr>
</table>
```

<a id="topic-5-3"></a>

### 5.3 常用标签补充

| 标签名 | 标签含义 | 单/双标签 |
| --- | --- | --- |
| br | 换行 | 单 |
| hr | 分隔 | 单 |
| pre | 按原文显示，一般用于在页面中嵌入大段代码 | 双 |

```html
<p>第一行<br>第二行</p>
<hr>
<pre>
function hello() {
  return "原文里的空格和换行会保留";
}
</pre>
```

注意点：

1. 不要用 `<br>` 来增加文本之间的行间隔，应使用后面即将学到的 CSS `margin` 属性。
2. `<hr>` 的语义是分隔。如果不想要语义，只是想画一条水平线，那么应当使用 CSS 完成。

<a id="module-6"></a>

## 6. 表单与嵌入内容

> **学习目标**：理解控件、数据名称、按钮、label 与 iframe。

<a id="topic-6-1"></a>

### 6.1 表单

#### 基本结构

这一节先记住表单的整体形式，表单控件稍后详细讲。

| 标签名 | 标签语义 | 常用属性 | 单/双标签 |
| --- | --- | --- | --- |
| form | 表单 | action、target、method | 双 |
| input | 输入框 | type、name | 单 |
| button | 按钮 | 本小节暂不涉及 | 双 |

`form` 的属性：

- `action`：指定表单的提交地址，需要与后端人员沟通后确定。
- `target`：控制表单提交后如何打开页面。`_self` 在本窗口打开，`_blank` 在新窗口打开。
- `method`：控制表单的提交方式。暂时只需了解，后面 Ajax 的课程会详细讲解。

`input` 的属性：

- `type`：设置输入框的类型。目前用到的值是 `text`，表示普通文本。
- `name`：指定提交数据的名字，需要与后端人员沟通后确定。

```html
<form action="https://www.baidu.com/s" target="_blank" method="get">
  <input type="text" name="wd">
  <button>去百度搜索</button>
</form>
```

这里 `action` 指向百度搜索，`name="wd"` 是百度用来接收关键词的名字。提交后按 `target="_blank"` 在新窗口打开结果。

#### 常用表单控件

表单控件就是用户在表单里填写、勾选、点击的那些部件。绝大多数控件都是 `<input>`，靠 `type` 区分成不同样子；少数控件有自己专门的标签，例如 `textarea`、`select`。

它们几乎都是行内元素，可以排在同一行。几乎每个控件都要写 `name`，因为提交时后端靠 `name` 来区分这是哪一项数据。

##### ① 文本输入框

```html
<input type="text">
```

普通单行文本框，输入什么就显示什么。常用属性如下：

| 属性 | 作用 |
| --- | --- |
| name | 数据的名称，提交时后端靠它取值 |
| value | 输入框的默认输入值 |
| maxlength | 输入框最大可输入长度 |

```html
<input type="text" name="username" value="游客" maxlength="10">
```

##### ② 密码输入框

```html
<input type="password">
```

密码框，输入的字符显示成圆点，避免旁人直接看到密码。常用属性如下：

| 属性 | 作用 |
| --- | --- |
| name | 数据的名称 |
| value | 输入框的默认输入值（一般不用，无意义） |
| maxlength | 输入框最大可输入长度 |

```html
<input type="password" name="pwd" maxlength="16">
```

密码框的 `value` 一般不写：预填一个明文默认密码既没意义也不安全。

##### ③ 单选框

同一组选项里只能选一个，例如性别。靠 `name` 相同来分组。

```html
<input type="radio" name="sex" value="female">女
<input type="radio" name="sex" value="male">男
```

| 属性 | 作用 |
| --- | --- |
| name | 数据的名称。**同一组的单选框 `name` 必须一样**，浏览器才知道它们互斥 |
| value | 这一项被选中后提交给后端的值 |
| checked | 默认选中。不用写属性值 |

```html
<input type="radio" name="sex" value="female">女
<input type="radio" name="sex" value="male" checked>男
```

注意点：

1. 同组 `name` 必须一致，否则每个单选框各自为政，能同时选中。
2. 选项后面的「女」「男」只是文字，点文字默认不会选中按钮。想点文字也能选中，用后面讲的 `<label>` 包起来。
3. 建议为每个选项明确写 `value`。省略时，被选中的单选框默认提交字符串 `on`，不是空值；整组没有选中项时，该组不会提交。参考 [MDN：单选框](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/radio)。

##### ④ 复选框

一组里可以选多个，例如爱好。同样用相同 `name` 归为一组。

```html
<input type="checkbox" name="hobby" value="eat">吃饭
<input type="checkbox" name="hobby" value="sleep" checked>睡觉
<input type="checkbox" name="hobby" value="code" checked>敲代码
```

| 属性 | 作用 |
| --- | --- |
| name | 数据的名称，同组保持一致 |
| value | 这一项被勾选后提交的值 |
| checked | 默认勾选。不用写属性值 |

和单选框的区别只有一个：复选框允许同时选多个，单选框同组互斥。

##### ⑤ 隐藏域

用户不可见的一个输入区域。作用是：提交表单的时候，携带一些固定的数据。

```html
<input type="hidden" name="tag" value="100">
```

| 属性 | 作用 |
| --- | --- |
| name | 指定数据的名称 |
| value | 指定的是真正提交的数据 |

页面上不显示这个输入框，但点提交时，`tag=100` 会和别的表单项一起交出去。

##### ⑥ 提交按钮

两种写法，点下去都会提交所在的表单：

```html
<input type="submit" value="点我提交表单">
<button>点我提交表单</button>
```

注意：

1. `button` 标签 `type` 属性的默认值是 `submit`。不写 `type` 时，点它就会提交表单。
2. 本例不需要给 `button` 写 `name`；提交按钮可以设置 `name`、`value`，点击该按钮提交时，这组数据也可一并提交。
3. 用 `input` 写的按钮，按钮上的文字靠 `value` 属性指定；用 `button` 写的按钮，文字写在标签体里。

##### ⑦ 重置按钮

把表单里已经填写的内容清回默认值。两种写法：

```html
<input type="reset" value="点我重置">
<button type="reset">点我重置</button>
```

注意点：

1. 本例不需要给 `button` 写 `name`；提交按钮可以设置 `name`、`value`，点击该按钮提交时，这组数据也可一并提交。
2. 用 `input` 写的按钮，按钮文字靠 `value` 属性指定；用 `button` 写的按钮，文字写在标签体里。

`button` 要写成 `type="reset"`。不写 `type` 时默认是 `submit`，点下去会提交表单，而不是重置。

##### ⑧ 普通按钮

点下去不提交、也不重置，一般留给后面的 JavaScript 用。两种写法：

```html
<input type="button" value="普通按钮">
<button type="button">普通按钮</button>
```

注意点：普通按钮的 `type` 值是 `button`。若不写 `type`，值是 `submit`，会引起表单的提交。

##### ⑨ 文本域

多行文本输入框，用 `<textarea>`，不是 `<input>`。默认内容写在标签体里。

```html
<textarea name="msg" rows="22" cols="3">我是文本域</textarea>
```

常用属性如下：

1. `rows` 属性：指定默认显示的行数，会影响文本域的高度。
2. `cols` 属性：指定默认显示的列数，会影响文本域的宽度。
3. 不使用 `type` 属性；常见属性包括 `name`、`disabled`、`maxlength`、`placeholder`。默认文本写在标签体中，不用 `value` 属性。参考 [MDN：textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/textarea)。

##### ⑩ 下拉框

点开是一个下拉菜单，用 `<select>` 包住，每个选项用 `<option>`。

```html
<select name="from">
  <option value="黑">黑龙江</option>
  <option value="辽">辽宁</option>
  <option value="吉">吉林</option>
  <option value="粤" selected>广东</option>
</select>
```

常用属性及注意事项：

1. `name` 属性：指定数据的名称，写在 `<select>` 上。
2. `<option>` 设置 `value` 属性。如果没有 `value`，提交的数据是 `option` 中间的文字；如果设置了 `value`，提交的数据就是 `value` 的值。建议设置 `value` 属性。
3. `<option>` 设置了 `selected` 属性，表示默认选中。上面例子里默认选中的是广东，提交的值是 `粤`。

##### ⑪ label 标签

`<label>` 是双标签，给表单控件配一段说明文字，并把这段文字和控件绑在一起。点文字时，浏览器会自动把焦点转到对应控件上：文本框、密码框会把光标放进去；单选框、复选框会被选中。

不绑的话，点「男」「女」这些字没有反应，必须点到那个小圆点才行。

两种绑定方式。

方式一：`label` 的 `for` 对准控件的 `id`。文字和控件可以分开写。

```html
<input type="radio" name="sex" id="nan" value="male">
<label for="nan">男</label>

<input type="radio" name="sex" id="nv" value="female">
<label for="nv">女</label>
```

方式二：把控件直接包进 `label` 里。不用写 `for`，也不用写 `id`。

```html
<label>
  <input type="radio" name="sex" value="male">男
</label>
<label>
  <input type="radio" name="sex" value="female">女
</label>
```

文本框同样可以绑。点「账户：」就能把光标放进输入框。

```html
<label for="user">账户：</label>
<input type="text" id="user" name="username">

<label>
  密码：<input type="password" name="pwd">
</label>
```

注意点：

1. 方式一里，`for` 的值必须和对应控件的 `id` 完全一样，包括大小写。对不上就绑不住。
2. `id` 在整个页面里不能重复。同一组单选框的 `name` 要相同，`id` 各自不同。
3. `for` 对准的是 `id`，不是 `name`。`name` 管提交给后端的数据名，`id` 管和 `label` 的绑定。
4. `<label>` 是行内元素，几个可以排在同一行。

#### 禁用表单控件

给表单控件的标签设置 `disabled`，即可禁用这个控件。禁用后看得见，但不能输入、也不能点击。`disabled` 通常不用写属性值。

`input`、`textarea`、`button`、`select`、`option` 都可以设置 `disabled` 属性。

```html
<input type="text" name="username" disabled>
<textarea name="msg" disabled>不能改</textarea>
<button type="submit" disabled>确认</button>
<select name="from" disabled>
  <option value="粤">广东</option>
  <option value="黑" disabled>黑龙江</option>
</select>
```

去掉 `disabled`，控件恢复可用。前面「标签上的属性」里已经写过一次，这里落到具体能用的表单标签上。

#### fieldset 与 legend 的使用（了解）

`fieldset` 可以为表单控件分组，`legend` 标签是分组的标题。浏览器会给这一组画一个框，标题嵌在框的上边。

```html
<fieldset>
  <legend>主要信息</legend>
  <label for="zhanghu">账户：</label>
  <input id="zhanghu" type="text" name="account" maxlength="10"><br>
  <label>
    密码：
    <input id="mima" type="password" name="pwd" maxlength="6">
  </label>
  <br>
  性别：
  <input type="radio" name="gender" value="male" id="nan">
  <label for="nan">男</label>
  <label>
    <input type="radio" name="gender" value="female" id="nv">女
  </label>
</fieldset>
```

- `<legend>` 写在 `<fieldset>` 里面，而且放在最前面，文字就是这组的标题。
- 这个例子把上一节的两种 `label` 绑法都用上了：账户、男用 `for` 对 `id`；密码、女把控件包在 `label` 里。
- 这一节标了「了解」，知道能分组、标题用 `legend` 即可。

#### 表单总结

| 标签名 | 标签语义 | 常用属性 | 单/双标签 |
| --- | --- | --- | --- |
| form | 表单 | `action`：表单要提交的地址。<br>`target`：跳转的新地址的打开方式，值：`_self`、`_blank`。<br>`method`：请求方式，可选值：`get`、`post` | 双 |
| input | 多种形式的表单控件 | `type`：指定表单控件的类型。可选值：`text`、`password`、`radio`、`checkbox`、`hidden`、`submit`、`reset`、`button` 等。<br>`name`：指定数据名称。<br>`value`：输入框是默认输入的值；单选和复选框是实际提交的数据；按钮是按钮上的文字。<br>`disabled`：设置表单控件不可用。<br>`maxlength`：用于输入框，设置最大可输入长度。<br>`checked`：用于单选按钮和复选框，默认选中 | 单 |
| textarea | 文本域 | `name`：指定数据名称。<br>`rows`：指定默认显示的行数，影响文本域的高度。<br>`cols`：指定默认显示的列数，影响文本域的宽度。<br>`disabled`：设置表单控件不可用 | 双 |
| select | 下拉框 | `name`：指定数据名称。<br>`disabled`：设置整个下拉框不可用 | 双 |
| option | 下拉框的选项 | `disabled`：设置下拉选项不可用。<br>`value`：该选项提交的数据。不指定 `value`，会把标签中的内容作为提交数据。<br>`selected`：默认选中 | 双 |
| button | 按钮 | `disabled`：设置按钮不可用。<br>`type`：设置按钮的类型。值：`submit`（默认）、`reset`、`button` | 双 |
| label | 与表单控件做关联 | `for`：值与要关联的表单控件的 `id` 值相同 | 双 |
| fieldset | 表单控件分组 | | 双 |
| legend | 分组名称 | | 双 |

<a id="topic-6-2"></a>

### 6.2 框架标签

`<iframe>` 是框架，用来在当前网页里嵌入另一个文件。双标签。

| 标签名 | 功能和语义 | 属性 | 单/双标签 |
| --- | --- | --- | --- |
| iframe | 框架（在网页中嵌入其他文件） | `name`：框架名字，可以与 `target` 属性配合。<br>`width`：框架的宽。<br>`height`：框架的高。<br>`frameborder`：是否显示边框，值：`0` 或者 `1` | 双 |

嵌入的地址写在 `src` 上：

```html
<iframe src="ad.html" name="show" width="400" height="300" frameborder="0"></iframe>
```

实际应用：

1. 在网页中嵌入广告。
2. 与超链接或表单的 `target` 配合，展示不同的内容。`iframe` 的 `name` 和链接、表单的 `target` 写成同一个名字，点击或提交后，新页面出现在这个框架里，而不是整页跳走。

```html
<iframe src="home.html" name="show" width="600" height="400" frameborder="1"></iframe>
<a href="news.html" target="show">新闻</a>
<form action="result.html" target="show">
  <input type="text" name="wd">
  <button>提交</button>
</form>
```

<a id="module-7"></a>

## 7. 字符、全局属性与元信息

> **学习目标**：查阅特殊字符、全局属性和 meta 配置。

<a id="topic-7-1"></a>

### 7.1 常见字符实体

浏览器会把源码里连续的空格、回车折成一个空格。`<`、`>`、`&` 又会被当成标签符号。要在页面上原样显示这些字符，就写成字符实体。每种实体有两种写法：实体名称、实体编号，都以 `;` 结尾。

课件用框标出的是要记住的：空格、小于号、大于号、和号、元、版权、乘号、除号。

| 显示 | 描述 | 实体名称 | 实体编号 |
| --- | --- | --- | --- |
| 空格 | 空格 | `&nbsp;` | `&#160;` |
| < | 小于号 | `&lt;` | `&#60;` |
| > | 大于号 | `&gt;` | `&#62;` |
| & | 和号 | `&amp;` | `&#38;` |
| " | 引号 | `&quot;` | `&#34;` |
| ´ | 锐音符 | `&acute;` | `&#180;` |
| ¢ | 分（cent） | `&cent;` | `&#162;` |
| £ | 磅（pound） | `&pound;` | `&#163;` |
| ¥ | 元（yen） | `&yen;` | `&#165;` |
| € | 欧元（euro） | `&euro;` | `&#8364;` |
| © | 版权（copyright） | `&copy;` | `&#169;` |
| ® | 注册商标 | `&reg;` | `&#174;` |
| ™ | 商标 | `&trade;` | `&#8482;` |
| × | 乘号 | `&times;` | `&#215;` |
| ÷ | 除号 | `&divide;` | `&#247;` |

```html
<p>空格不合并：A&nbsp;&nbsp;&nbsp;B</p>
<p>要显示标签符号：1 &lt; 2 &amp; 3 &gt; 0</p>
<p>价格：&yen;100&nbsp;&nbsp;版权：&copy;</p>
```

完整实体列表见 HTML Standard：<https://html.spec.whatwg.org/multipage/named-characters.html>

<a id="topic-7-2"></a>

### 7.2 HTML 全局属性

全局属性可用于所有 HTML 元素，不专属于某一个标签；部分属性在某些元素上可能没有可见效果。参考 [MDN：全局属性](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes)。

| 属性名 | 含义 |
| --- | --- |
| id | 给标签指定唯一标识。`id` 不能重复。可以让 `label` 与表单控件关联，也可以和 CSS、JavaScript 配合 |
| class | 给标签指定类名，随后通过 CSS 给标签设置样式 |
| style | 给标签设置 CSS 样式 |
| dir | 内容的方向，值：`ltr`、`rtl` |
| title | 给标签设置一个文字提示，鼠标停上去能看到。超链接和图片用得比较多 |
| lang | 给标签指定语言。具体规范和可选值见前面的 `html lang` |

```html
<p id="intro" class="text" style="color: red;" title="第一段" lang="zh-CN" dir="ltr">
  尚硅谷
</p>
```

- `id` 在整个页面里只能出现一次。同一组单选框的 `name` 相同，`id` 各自不同。
- `class` 可以重复，多个标签用同一个类名，就能套同一套样式。一个标签也可以写多个类名，用空格分开：`class="text red"`。
- `style` 把样式直接写在标签上。成片的样式仍放到 CSS 里，用 `class` 来套。

完整的全局属性列表见 MDN：<https://developer.mozilla.org/zh-CN/docs/Web/HTML/Reference/Global_attributes>

<a id="topic-7-3"></a>

### 7.3 meta 元信息

`<meta>` 是单标签，写在 `<head>` 里，用来配置页面本身的信息。下面这些 `content` 里的中文是课件在说明该填什么，真正写页面时换成自己的内容。

#### 配置字符编码

```html
<meta charset="utf-8">
```

和前面「一个 HTML 页面的开头」里的 `meta charset` 是同一件事。文件本身也要存成 UTF-8，否则中文会乱码。

#### 针对 IE 浏览器的兼容性配置

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

让 IE 用最新的渲染方式打开页面。

#### 针对移动端的配置

移动端课程会再详细讲。

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

#### 配置网页关键字

```html
<meta name="keywords" content="8-12个以英文逗号隔开的单词/词语">
```

`content` 里写 8 到 12 个词，用英文逗号隔开。

#### 配置网页描述信息

```html
<meta name="description" content="80字以内的一段话，与网站内容相关">
```

`content` 里写一段和网站内容相关的话，80 字以内。

#### 针对搜索引擎爬虫配置

```html
<meta name="robots" content="此处可选值见下表">
```

`content` 换成下表里的值，可以写多个，用英文逗号隔开，例如 `content="index, follow"`。

| 值 | 描述 |
| --- | --- |
| index | 允许搜索爬虫索引此页面 |
| noindex | 要求搜索爬虫不索引此页面 |
| follow | 允许搜索爬虫跟随此页面上的链接 |
| nofollow | 要求搜索爬虫不跟随此页面上的链接 |
| all | 与 `index, follow` 等价 |
| none | 与 `noindex, nofollow` 等价 |
| noarchive | 要求搜索引擎不缓存页面内容 |
| nocache | `noarchive` 的替代名称 |

#### 配置网页作者

```html
<meta name="author" content="tony">
```

#### 配置网页生成工具

```html
<meta name="generator" content="Visual Studio Code">
```

#### 配置定义网页版权信息

```html
<meta name="copyright" content="2023-2027©版权所有">
```

#### 配置网页自动刷新

```html
<meta http-equiv="refresh" content="10;url=http://www.baidu.com">
```

`10` 是秒数。到点后打开 `url` 后面的地址。不写 `url` 时，到点刷新的是当前页。

---

<a id="css-roadmap"></a>

## 8. CSS 学习路线（待补充）

本份原始笔记尚未包含系统的 CSS 章节。后续可按下面的顺序继续记录：

| 顺序 | 主题 | 要解决的问题 |
| --- | --- | --- |
| 1 | CSS 引入方式与选择器 | 样式写在哪里，如何选中元素 |
| 2 | 层叠、优先级与继承 | 多条样式冲突时哪条生效 |
| 3 | 颜色、字体与文本 | 如何控制文字与视觉样式 |
| 4 | 盒模型与尺寸 | 内容、内边距、边框、外边距的关系 |
| 5 | display 与定位 | 如何控制元素占位和位置 |
| 6 | Flexbox 与 Grid | 如何实现常用页面布局 |
| 7 | 响应式与媒体查询 | 如何适配手机和桌面屏幕 |

## 整理与勘误说明

- 统一原稿中不连续的章节编号，补全架构示意图的代码围栏和表格表头。
- 修正图片宽高属性、单选框默认值、全局属性适用范围，以及按钮与文本域的部分说明。
- 保留课堂中的简化嵌套记法，同时明确以 HTML 内容模型为准。
- 补充现代浏览器对 WebP 的支持说明，纠正字符实体表中锐音符的名称。

图片的宽高属性应写无单位整数，`alt` 用于提供替代文本。参见 [MDN：img](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/img)。按钮的 `name`/`value` 可参与表单提交。参见 [MDN：button](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/button)。WebP 的格式特性与兼容性可查阅 [MDN：图片格式指南](https://developer.mozilla.org/en-US/docs/Web/Media/Guides/Formats/Image_types)。

[返回学习地图](#学习地图) · [前端专区](README.md) · [学习笔记总目录](../README.md)
