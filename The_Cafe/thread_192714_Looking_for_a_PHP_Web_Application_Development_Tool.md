---
title: "Looking for a PHP Web Application Development Tool"
date: 2006-06-09
forum: The Cafe
---

### Post by crumja on 2006-06-09
I'm currently planning a web application of medium complexity. It will involve MySQL database access, parsing of complex database information, display of results to variables in a dynamic page. There will be also lots of drop down menus, buttons, entries, and other UI elements.

Originally I was going to do this on php, the language I was most familiar with (out of asp, jsp, and php). However, my previous experiences with php were replete with endless googling for precompiled solutions or modules for creating database objects, uploading files, resizing images, and authenticating users.

All this was a real pain. Then on a browse through the web looking for a good IDE for php, I found Sun Java Studio Creator. The product guide was amazing! I mean, everything that I had been scrambling for and trying to find was now automated. Yes, I can just drag and drop menus, UI widgets, tables, and feed into them data drawn from a database. Database access is also precoded and looks to be very easy to use. All this looks like it will significantly boost my productivity.

However, I don't have much experience in Java, so I'm asking the community if there are any good PHP dev tools that allow easy drag and drop of html ui elements, database access, and interface that with backend code. In short, is there a visual designer for php that incorporates a php backend?

---

### Post by rejser on 2006-06-09
There is always Zend studio, but it costs a buck
[http://www.zend.com/](http://www.zend.com/)

---

### Post by adamkane on 2006-06-09
You'll find that most programmer's say that all you need is a text-highlighting application like bluefish. All-in-one IDEs never seem to be as useful as one would expect.

---

### Post by paul.maddox on 2006-06-09
[QUOTE=rejser]There is always Zend studio, but it costs a buck
[http://www.zend.com/](http://www.zend.com/)[/QUOTE]

Our company uses Zend, it really is the best out there but on the downside it isn't free.

For managing MySQL databases we tend to use Navicat, again another product that isn't free but very good.

Both products have 30day trials available on their websites.

---

### Post by ember on 2006-06-09
I use Zend Studio, too. Though a little sluggish sometimes, it is the most functional and useful PHP IDE I know. However it does not offer draggable HTML UI elements (which doesn't trouble me much).

Yet my experience with IDEs with RAD-Tools for database development is that the abstraction level is not high enough. I would recommend you the combination of PHP, AdoDB and Smarty - which is what I use for some years. This will enable you to design flexible solutions that enforce the MVC pattern - additionally you can easily add AJAX flavour to your application using HTML_AJAX (from PEAR) and the script.aculo.us JS-library.

---

### Post by !nkubus on 2006-06-09
[QUOTE=ember]I use Zend Studio, too. Though a little sluggish sometimes, it is the most functional and useful PHP IDE I know. However it does not offer draggable HTML UI elements (which doesn't trouble me much).

Yet my experience with IDEs with RAD-Tools for database development is that the abstraction level is not high enough. I would recommend you the combination of PHP, AdoDB and Smarty - which is what I use for some years. This will enable you to design flexible solutions that enforce the MVC pattern - additionally you can easily add AJAX flavour to your application using HTML_AJAX (from PEAR) and the script.aculo.us JS-library.[/QUOTE]

If you have a good machine I would suggest 

Eclipse with PHP plugins, + Mysql Plugin for eclipse.

[http://www.eclipse.org](http://www.eclipse.org)

For tons of plugins:
[http://www.eclipseplugincentral.com](http://www.eclipseplugincentral.com)


Hop it helps :)

---

### Post by megahertza on 2006-06-09
I use bluefish for highlighting. But for the whole drop and drag thing, I much prefer to build my own classes and function and reuse code over and over. I find it the only way to make the final product the exac way you want.

---

