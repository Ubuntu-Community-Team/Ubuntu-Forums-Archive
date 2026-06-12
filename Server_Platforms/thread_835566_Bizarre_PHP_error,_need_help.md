---
title: "Bizarre PHP error, need help"
date: 2008-06-20
forum: Server Platforms
---

### Post by gear_head on 2008-06-20
So i have Apache2 and PHP5 installed, and I checked the documentation to make sure everything is installed correctly and it is.

however, when I open up firefox and try to access a php page it tries to download it instead of viewing it as a web page.

Any idea what's going on here?

EDIT: update, it seems to be only one file. My other php scripts seem to be working just fine.

---

### Post by [vu] on 2008-06-20
It´s good your code? you know.. tags and that stuff?
Can you paste your code here?

---

### Post by robklg on 2008-06-20
It sounds like you forgot the AddHandler statement for php in your apache configuration...

Basically, apache doesn't have a handler defined for your .php files, and will thus not let them be interpreted by php

You need to install apache2-php5 or something...

As you have that... 

Take a look at /etc/apache2/mods-available

You see some php5 thing there?

Make a link to it from /etc/apache2/mods-enabled

Then reload apache

---

