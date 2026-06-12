---
title: "A little help on a website?"
date: 2008-05-28
forum: The Cafe
---

### Post by Old Marcus on 2008-05-28
Now, I'm not sure if this is the right place, but I'm sure somebody here will know. I'm making a website using a three column CSS layout and divider images to separate the columns.

[http://majicalyouth.110mb.com/](http://majicalyouth.110mb.com/)

(It's for a festival kid's area)

Now, if you look at the divider for the right hand column and the centre column it doesn't go all the way down. As far as I can tell, it's determined by the amount of content in the centre column. If you click on ride hire you'll notice it's all the way down to the bottom, due the the large amounts of Lipsum I've posted. Is there a way to stop it being decided by the amount of content and make it reach the bottom regardless?

Code:

XHTML:
```
<?php include('doctype.txt'); ?>

<html xmlns="http://www.w3.org/1999/xhtml">

<head>

<meta http-equiv="content-type" content="text/html; charset=utf-8" />

<title>Welcome to Majical Youth</title>

<?php include('css.txt'); ?>

</head>



<body>

<div id="wrapper">

<div id="header">

<?php include('header.txt'); ?>

</div>

<div id="container">

<div id="left">
<div id="nav">

<?php include('nav.txt'); ?>

</div>

</div>

<div id="right">

<h1>LIPSUM</h1>

<img src="http://www.lipsumgallery.com/admin/uploads/Lipsum%20logo%202.JPG" alt="Lipsum" />

<p>

Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Nullam lorem mauris, pretium at, dictum nec, aliquam non, felis. Etiam mollis sagittis lorem. Fusce nec velit. Donec id neque non erat rhoncus iaculis. Quisque dictum sem quis quam. Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Nulla commodo, neque eu ornare facilisis, quam metus vehicula est, non facilisis ante sem pretium elit. Quisque in sapien. Fusce rutrum diam at arcu. Aenean cursus, urna non mollis scelerisque, orci erat lacinia justo, eu posuere enim velit a lorem. In hac habitasse platea dictumst.

</p>

</div>
<div id="farright">
</div>

<div class="clearer"></div>

</div>

<div id="footer">

<?php include('footer.txt'); ?>

</div>

</div>

</body>

</html>
```

CSS:
```
html, body {

margin: 0px;

padding: 0px;

}

body {

font-family: Verdana, Arial, sans-serif;

font-size: 11px;

color: #000;

text-align: center;

line-height: 1.8em;

background-image: url(images/back.jpg);

}

#wrapper {

width: 80%;
min-height: 100%;

margin: 15px auto 15px auto;

padding: 0px;

text-align: left;

border: solid 4px #c00;

background-image:url(images/back.green.gif);
/*background-color: #090;*/

}

#container {

width: 100%;

height: 100%;

margin: 0px;

padding: 0px;

background-image: url(images/divider.gif);

background-repeat: repeat-y;

background-position: 200px 0px;

}

#left {

width: 160px;

height: auto;

float: left;

padding: 20px;

margin: 0px;

}

#right {

width: 530px;

height: auto;

float: left;

padding: 20px 20px 20px 20px;

margin: 0px;
background-image: url(images/divider.gif);
background-repeat: repeat-y;

background-position: 565px 0px;

}

#right p {

margin: 0px;

}

.clearer {

font-size: 0px;

height: 0px;

width: 100%;

display: block;

clear: both;

}

#footer {

padding: 5px;

margin: 0px;

border-top: solid 4px #c00;

text-align: center;

background-color: #0C0;
background-image:url(images/back.gif);

}
table {
width: 100%;
}
#farright {

width: 160px;

height: auto;

float: right;

padding: 20px;

margin: 0px;

}

```

#left is the left column, #right is the centre column, and #farright is the right column.
wrapper is the space inside the red box, and container is the space between the header and footer.

---

