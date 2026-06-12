---
title: "Setting up a web server with Ubuntu"
date: 2010-01-29
forum: Server Platforms
---

### Post by TheAlien on 2010-01-29
Hello!

I would like to know if there are any guides on the Internet to help setup a standard web server on the Ubuntu desktop edition. I'd like to have a secure web server that supports the same software as the average web host company does, like PHP, MySQL, and etc, so I can setup a functional website with discussion boards, and etc.

I'm using the desktop edition because I'm a utter noob on this, lol, and I need the GUI.

Or if anyone would like to just help me out and point me in the right direction, I'd be very grateful.

:)

---

### Post by noway2 on 2010-01-29
Try Apache.  If you do an internet search for 'howto apache' you will get more links to setup guides than you care to read.

---

### Post by openfly on 2010-01-29
Look for the word "lamp".  Being an acronym for Linux Apache MySQL PHP.

There's plenty of web dev friendly documentation on getting up and running quickly.

---

### Post by TheAlien on 2010-01-29
Thanks.

I've found this link:
[https://help.ubuntu.com/community/ApacheMySQLPHP#After%20installing%20PHP](https://help.ubuntu.com/community/ApacheMySQLPHP#After%20installing%20PHP)
As in LAMP

```
$ sudo tasksel install lamp-server
```It seems to contain everything I need to setup a web server.

If anyone have more to add about this package to help me setup a secure web server, please help me out and I will be grateful!

:)

---

### Post by KnottyMars on 2010-01-29
This has been the best tutorial I could find. It includes pictures and gives a pretty good step by step process for getting the server up and running with LAMP+SSH 

I copied the text and tested the process and it works like a champ. Hope this helps 

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

EDIT: and if you wanted to setup a mail server on that box, this another great step by step tutorial that I found. VERY detailed layout and may be overkill for most small servers, but I found it very useful. 

[http://flurdy.com/docs/postfix/edition7.html](http://flurdy.com/docs/postfix/edition7.html) 

Good luck!

---

