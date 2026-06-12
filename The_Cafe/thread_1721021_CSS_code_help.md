---
title: "CSS code help"
date: 2011-04-03
forum: The Cafe
---

### Post by numerounoredsoxfan on 2011-04-03
I am building a website and I cannot figure out what I need to do in order to make my website auto scale to size when people with a smaller monitor/browser look at it.  Please help.....

Here is my current CSS code:

```
/**
 * @file
 * @project 622
 * @package sftheme
 * @site app1
 */
 
/** 
 * ------------------------------------------------------------------
 * @section TYPOGRAPHY
 * ------------------------------------------------------------------
 */
 
h1, h2, h3, h4, h5, h6 {font-weight:normal;}
h1 {font-size:3em;line-height:1;margin-bottom:0.5em;}
h2 {font-size:2em;margin-bottom:0.75em;}
h3 {font-size:1.5em;line-height:1;margin-bottom:1em;}
h4 {font-size:1.2em;line-height:1.25;margin-bottom:1.25em;height:1.25em;}
h5 {font-size:1em;font-weight:bold;margin-bottom:1.5em;}
h6 {font-size:1em;font-weight:bold;}
p, form {margin:0 0 1.5em;padding:0;}
blockquote {margin:1.5em;}
sup, sub {line-height:0;}
address {margin:0 0 1.5em;}
pre, code {margin:1.5em 0;white-space:pre;}
pre, code, tt {line-height:1.5;}
li ul, li ol {margin:0 2.5em;padding:0;}
ul, ol {margin:0 1.5em 1.5em 3em;padding:0;}
ul {list-style-type:disc;}
ol {list-style-type:decimal;}
dl {margin:0 0 1.5em 0;}
dd {margin-left:1.5em;}
caption {margin:0; padding:.5em;}

/** 
 * ------------------------------------------------------------------
 * @section MAIN AREA
 * ------------------------------------------------------------------
 */
 
body {
    margin:0px;
    padding:0px;
    font-family:Arial, Helvetica, FreeSans, sans-serif;
    font-size:14px;
}

.sf_pagetitle {
    font-family:Garamond, "Palatino Linotype", "Book Antiqua", Palatino, FreeSerif, serif;
    font-size:28px;
    font-weight:bold;
    margin:0px 0px 10px;
    padding-bottom:2px;
}

.sf_pagetitle h1 {
    font-size:28px;
    font-weight:bold;
    margin:0px;
}

.sf_outer_wrapper {
    min-width:980px;
}

.sf_region1 {
    min-height:127px;
    height:auto !important;
    height:127px;
    background-repeat:no-repeat;
    width:100%;
    margin-left:-450px;
    float:right;
    display:inline;
}

.sf_region1:after {
    content:".";
    display:block;
    height:0;
    visibility:hidden;
    clear:both;
}

.sf_main_header {
    font-family:Garamond, "Palatino Linotype", "Book Antiqua", Palatino, FreeSerif, serif;
    font-size:48px;
    font-weight:bold;
    width:380px;
    padding-top:10px;
    padding-bottom:5px;
    margin-left:60px;
    float:left;
    display:inline;
}

/** 
 * @subsection navigation
 */
.sf_navigation .widget_header {
    display:none;
}

.sf_navigation {
    display:block;
    font-size:11px;
    text-transform:uppercase;
    padding-right:30px;
    margin-left:450px;
}

.sf_navigation ul {
    margin:0px;
    padding:0px;
    list-style-type:none;
    width:100%;
    min-height:10px;
    height:auto !important;
    height:10px;
    float:right;
}

.sf_navigation ul:after {
    content:".";
    display:block;
    height:0;
    visibility:hidden;
    clear:both;
}

.sf_navigation ul li {
    float: right;
    width: auto !important;
    width: 1%;
    margin:0px 1px 1px 0px;
    padding:0px;
    display:inline;
}

.sf_navigation ul li a {
    display: block;
    width: auto !important;
    width: 1%;
    white-space:nowrap;
    padding:8px 20px;
    margin:0px;
    text-decoration:none;
}

/** 
 * @subsection subnav
 */
.sf_navigation ul.subnav {
    padding:0px;
    margin:0px;
    margin-left:-1px;
    position: absolute;
    width: 150px;
    left: -999em;
    z-index:1000;
}

.sf_navigation ul.subnav li {
    float: left;
    width: 150px !important;
    margin:0px 0px 1px;
    padding:0px;
}

.sf_navigation li.sf_first_nav_item ul.subnav a {
    background-image:none;
}

.sf_navigation ul.subnav li.sf_last_nav_item_subnav {
    margin:0px;
    padding:0px;
}

.sf_navigation ul.subnav li a {
    display: block;
    width: 110px !important;
    padding:8px 20px;
    margin:0px;
    text-decoration:none;
    background-image:none;
    white-space:normal;
}

.sf_navigation ul.subnav li a:visited {
    background-image:none;
}

.sf_navigation ul.subnav li a:hover {
    background-image:none;
}

#Nav1 li:hover ul,
#Nav1 li.sfhover ul { /* lists nested under hovered list items */
    left: auto;
}

#Nav1 li:hover,
#Nav1 li.hover {
    position: static;
}

#Nav1 iframe {
    position: absolute;
    left: 0;
    top: 0;
    z-index: 0;
 filter: progid:DXImageTransform.Microsoft.Alpha(style=0, opacity=0);
}

/** 
 * @subsection main
 */
.sf_wrapper {
    position:relative;
    background-image:url(images/622_right_shad.gif);
    background-repeat:no-repeat;
    background-position:right top;
    min-height:1%;
    height:auto !important;
    height:1%;
    clear:both;
}

.sf_wrapper:after {
    content: ".";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
}

/** 
 * @subsection horizontal shadow
 */
.sf_extra4 {
    background-image:url(images/622_horizontal_shad.png);
    display:block;
    width:100%;
    height:40px;
    position:absolute;
    left:0;
    top:0;
}

* html .sf_extra4 {
 behavior: expression((this.runtimeStyle.behavior="none")&&(this.pngSet?this.pngSet=true:(this.nodeName == "IMG" && this.src.toLowerCase().indexOf('.png')>-1?(this.runtimeStyle.backgroundImage = "none", this.runtimeStyle.filter = "progid:DXImageTransform.Microsoft.AlphaImageLoader(src='" + this.src + "', sizingMethod='image')", this.src = "images/spacer.gif"):(this.origBg = this.origBg? this.origBg :this.currentStyle.backgroundImage.toString().replace('url("', '').replace('")', ''), this.runtimeStyle.filter = "progid:DXImageTransform.Microsoft.AlphaImageLoader(src='" + this.origBg + "', sizingMethod='scale')", this.runtimeStyle.backgroundImage = "none")), this.pngSet=true));
}

/** 
 * @subsection main content
 */
.sf_main_wrapper {
    width:100%;
}

.sf_main {
    background-image:url(images/622_left_shad.gif);
    background-repeat:no-repeat;
    padding:40px 60px;
    min-height:300px;
    height:auto !important;
    height:300px;
}

/** 
 * @subsection region10
 */
.sf_footer {
    text-align:right;
    font-size:11px;
    text-transform:uppercase;
    padding:10px 30px;
}

.sf_footer:after {
    content: ".";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
}

.sf_banner {
    text-align:right;
    font-size:9px;
    text-transform:uppercase;
    float:right;
    padding:10px 30px;
}

.sf_banner img {
    margin-bottom:3px;
}

.sf_banner #bannerLink {
    width:250px;
}

/** 
 * @subsection buttons
 */
.btn {
    margin:2px 0px;
}

/** 
 * ------------------------------------------------------------------
 * @section SIDEBAR AREA
 * ------------------------------------------------------------------
 */
 .sf_region7 {
    font-size:12px;
}

/** 
 * @subsection widgets
 */
.widget {
    margin-bottom:10px;
}

.widget:after {
    content: ".";
    display:block;
    visibility:hidden;
    height:0;
    clear:both;
}

.widget_header {
    font-family:Garamond, "Palatino Linotype", "Book Antiqua", Palatino, FreeSerif, serif;
    font-weight:bold;
    margin-bottom:10px;
    font-size:18px;
}

.widget_content:after {
    content: ".";
    display:block;
    visibility:hidden;
    height:0;
    clear:both;
}

.widgetset .widget_content label {
    margin:0;
    padding:0;
    display:block;
}

.widgetset .widget_content form {
    margin:0;
    padding:0;
}

.widgetset .widget_content select,
.widgetset .widget_content input[type="text"] {
    width:178px;
    border-style:solid;
    border-width:1px;
    padding:1px 0px;
}

.widgetset ul,
.widgetset ol {
    margin:0px;
    padding:0px;
    list-style-type:none;
}

.widget li {
    margin:6px 0px;
    padding:0px;
}

.widgetset .widget_content .form_item {
    margin:6px 0px;
    padding:0;
}
```

---

### Post by Untitled_No4 on 2011-04-04
Hard to read a CSS file, but here's my attempt.

As you may know, CSS elements inherit some attributes from their parents. If you want a certain Div to be 10% of its parent, you have to go all the way to the first parent and define a width. So you need to go all the way up to html. 
For instance, the following code will create a layout which has a blue column on the left which is 25% of the browser width, and will change upon browser resize. 

```

<html>
<head>
<style type="text/css">
html, body {
  width: 100%;
  height: 100%;
}

#Container {
  width: 100%;
  height: 100%;
  background: red;
}

#ColLeft {
  width: 25%;
  height: 100%;
  background: blue;
}
</style>
</head>
<body>
<div id="Container">
    <div id="ColLeft">

    </div>
</div>
</body>
</html>

```

As you can see, I started with html and body, gave them 100% width (and height), and the same with the container. Then anything in the container can be styled to be a % of width of the container.

One last thing: reset your css before you start, it will save you headache and time later. Read here (for code too): [http://developer.yahoo.com/yui/reset/](http://developer.yahoo.com/yui/reset/)

---

### Post by linuxforartists on 2011-04-04
In the future, you might want to check out [DocType]("http://doctype.com/").  It's an awesome question & answer website for web designers.  

I was once building a website and wrestling with a CSS display problem in Firefox.  I posted a question on DocType, and got a solution in less than 15 minutes.  Amazing.

---

### Post by fdrake on 2011-04-17
You should always use relative measures not absolutes!

---

