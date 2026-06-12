---
title: "Apache and css"
date: 2007-04-12
forum: Server Platforms
---

### Post by tbuss on 2007-04-12
I know this might seem like a very simple question, but I cannot figure out how to load style sheets for my my pages? I have looked everywhere for information on this. Is this a module that needs to be loaded? I tried adding *AddType text/css .css* to my httpd.conf; I also tried putting the css files in the /var/www/apache2-default dir with the index.html and changing the links in the index.html to /var/www/apache2-default/style.css/ and /var/www/apache2-default/color.css. Should I just forget about trying to use external stylesheets and just list them in the header section of each html page I use?

---

### Post by jfinkels on 2007-04-12
CSS have nothing to do with Apache. Just put your CSS file in the same directory as the page you want to load, and link to the CSS file from your HTML file. Put this in the head of your HTML
```

<link rel="stylesheet" type="text/css" href="mystyle.css">

```
where "mystyle.css" is the name of your stylesheet!

EDIT:

[http://w3schools.com/css/default.asp](http://w3schools.com/css/default.asp) has excellent tutorial for web programming

---

### Post by tbuss on 2007-04-12
> CSS have nothing to do with Apache. Just put your CSS file in the same directory as the page you want to load, and link to the CSS file from your HTML file. Put this in the head of your HTML
Code:

<link rel="stylesheet" type="text/css" href="mystyle.css">

where "mystyle.css" is the name of your stylesheet!

[B]
Right, I have tried that already:[/B]
```
<head>

  <title>Bussell: home</title>
  <meta http-equiv="content-type" content="text/html; charset=iso-8859-1" />

  <!-- **** layout stylesheet **** -->
  <link rel="stylesheet" type="text/css" href="/var/www/apache2-default/style.css" />

  <!-- **** colour scheme stylesheet **** -->
  <link rel="stylesheet" type="text/css" href="/var/www/apache2-default/colour.css" />

</head>

```

**All three files are located in var/www/apache2-default. (style.css color.css index.html)** 
**but page still loads plain**?

---

### Post by jfinkels on 2007-04-12
perhaps instead of the full filesystem path to your stylesheets, try doing the relative path with respect to the HTML file, so instead of 

```

href="/var/www/apache-default/style.css"

```
do
```

href="./style.css"

```

---

### Post by jfinkels on 2007-04-12
also, you may want to consider making a new index.html in /var/www , that's the standard way of doing things. It might be better to start with a whole new page than to try and mess with a default page that already exists. Also also, make sure your DocumentRoot is correct

---

### Post by tbuss on 2007-04-12
I have tried relaitive as well, the page is orginal but I have not considered looking at DocumentRoot

Thanks for all your help and advice

---

### Post by tbuss on 2007-04-12
**jfinkels:**

I figured it out. I was using a template and I had renamed the colour.css to color.css All my links were pointing to colour.css instead of color.css Now I feel really dumb :P Thanks again for your help

---

### Post by jfinkels on 2007-04-13
> **tbuss said:**
> **jfinkels:**

I figured it out. I was using a template and I had renamed the colour.css to color.css All my links were pointing to colour.css instead of color.css Now I feel really dumb :P Thanks again for your help

Heh, I knew it would be something silly like that. That stuff always happens. 

Speaking of thatm, here's the way I go about solving most computer problems:

1. Is it on fire? If not...
2. Is it plugged in? If not...
3. Is it turned on?

You'd be amazed how many problems can be solved this way!

---

