---
title: "Make css page minimum height to not cover up sidebar"
date: 2009-06-27
forum: The Cafe
---

### Post by zorocke on 2009-06-27
I'm making a two column layout for my site, but the problem is if the content in the left column is not long enough then the right column just doesn't show it's entire content. ](*,)
Any ideas on how to fix this?

Here's my CSS
```

/*  
Theme Name: Spring
Theme URI: http://www.spocore.com
Description: This is my theme
Version: 1.0
Author: Steven Spohrer
*/
body {
width: 800px;
margin:0 auto;
margin-top:0px;

}

/* ----- HEADER ----- */
#header {

height:80px;
margin: 0px;
padding: 0px;
border-bottom: 1px solid #c7c7c7;
}
#header-nav {
position:absolute;
left:600px;
top:40px;
height: 30px;
width: 440px;
}
#header-nav li
{
padding-top: 0px;
display: inline;
list-style-type: none;
padding-right: 5px;
padding-left: 5px;
border-right: 1px solid #7c7c7c;
float: right;

}
#header-nav li a{
color: #232323;
text-decoration:none;
}




/*--- Header Two ---- */
#header2 {
width 700px;
height: 300px;
background-image: url(h2.png);
background-repeat: no-repeat;
border-bottom: 1px solid #c7c7c7;

}


/* ----- MAIN CONTENT ----- */

#container { 
width:798px;
height: auto !important;
height: 100%;

padding-left:8px;
padding-right:13px;
overflow: hidden;
padding-bottom: auto !important;
background-image: url(container.png);
background-repeat: repeat-y 0 0;
}

/*---Content Left ---*/
#content-left{
float: left;
width: 72%;
padding-bottom: 5000px;
margin-bottom: -5000px;
padding-left: 15px;

}
#content-left h3 a{
color: #008100;
font-size: 1.5em;
text-decoration: none;
}
#content-left a{
color: #006000;
}
/* ---- Blog Posts */
#content-left .postheading{
font-size: 12px;
}

/*---Content Right --- */
#content-right{
background-image: url(rightpush.png);
background-repeat: repeat-y;
float:right;
width: 23%;
font-size: 1em;
padding-bottom: 5000px;
margin-bottom: -5000px;
padding-bottom: 25px;

padding-right: 10px;
padding-top: 10px;
height: 600px;
height: auto !important;
height: 100%;
overflow: hidden;

}
#content-right h3{
margin-top:0px;
background-color: #e5eecc;
color:black;
font-size: 17px;
font-weight: 100;
padding-left: 15px;

border: 1px solid #d7d7d7;
margin-bottom: 0px;
}
#content-right ul{

margin-left: 0px;
padding-left: 0px;
margin-top: 0px;
list-style: none;
}
#content-right li a{
background-color: #f5ffdb;
list-style: none;
display: block;
border-bottom: 1px solid #d7d7d7;

padding-top: 3px;
padding-bottom: 3px;

border-left: 1px solid #d7d7d7;
border-right: 1px solid #d7d7d7;
border-bottom: 1px solid #d7d7d7;

padding-left: 15px;
color: black;
font-size: 15px;
}
#content-right li a:hover{

}

/*Search form*/
#search input
{
margin-bottom: 5px;
color: #781351;
background: #f3f7e9;
border: 1px solid #d7d7d7;
}

/* ----- Footer ----- */
#footer { 
width:800px;
height:50px;
background-color:#e1e1e1;
margin-top:0px;
clear: both;
}


```
It's a little bit messy, and i've been trying a lot of things to get this to work. So if some stuff is there that shouldn't be, just ignore that. 

thanks

---

### Post by crush304 on 2009-06-27
```

body{
    width:800px;
    margin:auto;
}
#leftcolumn{
    float:left;
    width:70%;
}
#rightcolumn{
    float:left;
    width:29%;
}

```

---

### Post by zorocke on 2009-06-28
Thank you. I guess I just needed to remove all the heights and overflows, and everything else. It works great now.

---

