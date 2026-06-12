---
title: "What's the deal with yui.yahooapis.com"
date: 2009-03-22
forum: The Cafe
---

### Post by t0p on 2009-03-22
Why is it that, whenever I navigate to a link on this site, my computer transfers data to/from [yui.yahooapis.com]("http://yui.yahooapis.com")?  Is the owner of this site secretly sharing our user info with a mysterious third party. (Ooo-Eee-Ooo)

If you go to that address, you'll find it is 404 Not Found... according to Yahoo!  The site [yahooapis.com]("http://yahooapis.com") leads to [developer.yahoo.com]("http://developer.yahoo.com"), which is home page for the Yahoo Developer Network.

Why this data transfer with Yahoo developers?  Inquiring minds want to know.

---

### Post by I-75 on 2009-03-22
Maybe that is related to one of the "spiders" that are actually a part of our user base?

Currently Active Users: 12914 (911 members and 11941 guests and 62 Spiders)

---

### Post by sisco311 on 2009-03-22
[quote=ubuntu-geek]q. Why is my browser trying to connect to [http://yui.yahooapis.com](http://yui.yahooapis.com) when browsing ubuntu forums?
A. The new forum software uses yahoo's javascript libraries. [http://developer.yahoo.com/yui/articles/hosting/](http://developer.yahoo.com/yui/articles/hosting/)
a. You can also find information here about the use of the yui in vbulletin. [http://www.vbulletin.com/forum/showp...7&postcount=20](http://www.vbulletin.com/forum/showp...7&postcount=20)[/quote]

[thread]4761308[/thread]

;)

---

### Post by cardinals_fan on 2009-03-22
[http://ubuntuforums.org/showthread.php?t=904808](http://ubuntuforums.org/showthread.php?t=904808)

In short, it lets the admins host javascript off the forum servers.

---

### Post by t0p on 2009-03-22
Thanks, **sisco311** and **cardinals_fan**.

But get this: try to navigate to [yui.yahooapis.com]("http://yui.yahooapis.com") and you get 404 Not Found error.  That address is no longer extant.  So why continue sending data there?

---

### Post by Mehall on 2009-03-22
> **t0p said:**
> Thanks, **sisco311** and **cardinals_fan**.

But get this: try to navigate to [yui.yahooapis.com]("http://yui.yahooapis.com") and you get 404 Not Found error.  That address is no longer extant.  So why continue sending data there?

404 = no index.html home.html .php, .aspx, etc, etc.

Just because something has nothing to show to you, doesn't mean it's not doing anything.

---

### Post by Polygon on 2009-03-23
yeah, yahooapis is similiar to googleapis.com, it just has some useful javascript api's that people can link to and use without having to write their own.

and a 404 means its just not responding to a http request, it doesn't mean it doesn't respond to other types of requests.

---

