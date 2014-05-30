HTML 编码规范
=============
此为前端开发团队遵循和约定的**HTML 编码规范**，意在提高代码的规范性和可维护性。

## 说明

文档中使用的关键字「MUST」,「MUST NOT」,「SHOULD」,「SHOULD NOT」,「RECOMMENDED」,「MAY」在[RFC2119](http://oss.org.cn/man/develop/rfc/RFC2119.txt)中有说明。

> 还未定稿，对规范中有不赞同的欢迎[提出issues](https://github.com/yutouxiuxiu/code-style/issues/new)(请添加 `HTML` 标签)讨论。

## 规则

* 新起一行的标签，或者在一行内写不下的内容「MUST」和父标签保持一次缩进。

    ```html
    // bad
    <!DOCTYPE html>
    <html>
    <head>
    <title>abc</title>
    </head>
    <body>
    <ul>
    <li>Dog</li>
    <li>Cat</li>
    </ul>
    </body>

    // good
    <!DOCTYPE html>
    <html>
        <head>
            <title>abc</title>
        </head>
        <body>
            <ul>
                <li>Dog</li>
                <li>Cat</li>
            </ul>
        </body>
    </html>
    ```
* 标签属性值「MUST」使用双引号。

    ```html
    // bad
    <a class='maia-button maia-button-secondary'>Sign in</a>

    // good
    <a class="maia-button maia-button-secondary">Sign in</a>
    ```

* 文档类型声明「MUST」使用 HTML5。

    ```html
    // good
    <!DOCTYPE html>
    ```

* HTML 的标签使用「SHOULD」遵循标签的语义。

    ```html
    // bad
    <div onclick="goToRecommendations();">All recommendations</div>

    // good
    <a href="recommendations/">All recommendations</a>
    ```

* `<img>` 标签「SHOULD」添加 `alt` 属性来增强可访问性。

    ```html
    // bad
    <img src="spreadsheet.png">

    // good
    <img src="spreadsheet.png" alt="Spreadsheet screenshot.">
    ```

* 「SHOULD」将 HTML 中的内容(html)、表现(css)和行为(javascript)分离，HTML 标签只「SHOULD」用于定义内容。

    ```html
    // bad
    <!DOCTYPE html>
    <title>HTML sucks</title>
    <link rel="stylesheet" href="base.css" media="screen">
    <link rel="stylesheet" href="grid.css" media="screen">
    <link rel="stylesheet" href="print.css" media="print">
    <h1 style="font-size: 1em;">HTML sucks</h1>
    <p>I’ve read about this on a few sites but now I’m sure:
        <u>HTML is stupid!!1</u>
    <center>I can’t believe there’s no way to control the styling of
        my website without doing everything all over again!</center>

    // good
    <!DOCTYPE html>
    <title>My first CSS-only redesign</title>
    <link rel="stylesheet" href="default.css">
    <h1>My first CSS-only redesign</h1>
    <p>I’ve read about this on a few sites but today I’m actually
        doing it: separating concerns and avoiding anything in the HTML of
        my website that is presentational.
    <p>It’s awesome!
    ```

* 「SHOULD」省略样式标签(link/style)和脚本标签(script)中的type属性。

    ```html
    // bad
    <link rel="stylesheet" href="//www.google.com/css/maia.css"
    type="text/css">
    <script src="//www.google.com/js/gweb/analytics/autotrack.js"
    type="text/javascript"></script>
    <style type="text/css">
        .author{}
    </style>
    
    // good
    <link rel="stylesheet" href="//www.google.com/css/maia.css">
    <script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
    <style>
        .author{}
    </style>
    ```

* URL 的写法「SHOULD」省掉协议，这样能更好地适应 http 和 https。

    ```html
    //good
    <script src="//fex.baidu.com/example.js"></script>
    ```

* 「SHOULD」省略自闭合标签结尾的斜杠。

    ```html
    // bad
    <img src="spreadsheet.png" alt="Spreadsheet screenshot." />

    // good
    <img src="spreadsheet.png" alt="Spreadsheet screenshot.">
    ```

* 应该「SHOULD」启用 IE Edge 模式。

    ```html
    <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    ```

* HTML 文件编码以及 `meta` 标签编码应该「SHOULD」统一为 `UTF-8`，文件内容编码为 UTF-8（无 BOM）。

    ```html
    <meta charset="UTF-8">
    ```

* 「SHOULD NOT」使用实体，对于 UTF-8 的页面，使用实体意义不大，反而降低了可维护性。

    ```
    // bad
    Euro is &ldquo;&eur;&rdquo;.
    
    // good
    Euro is “€”.
    ```

* HTML 文件编码声明「MUST」在 `<title>` 之前，避免编码检测出错导致的问题。

    ```html
    // bad
    <title>中文</title>
    <meta charset="UTF=8">

    // good
    <meta charset="UTF=8">
    <title>中文</title>
    ```

* 布尔类型的属性「SHOULD NOT」添加属性值。

    ```html
    // bad
    <input type="text" disabled="true">

    <input type="checkbox" value="1" checked="true">

    <select>
        <option value="1" selected="true">1</option>
    </select>

    // good
    <input type="text" disabled>

    <input type="checkbox" value="1" checked>

    <select>
        <option value="1" selected>1</option>
    </select>
    ```
