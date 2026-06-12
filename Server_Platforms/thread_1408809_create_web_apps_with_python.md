---
title: "create web apps with python?"
date: 2010-02-16
forum: Server Platforms
---

### Post by ubudog on 2010-02-16
Hello, can I use a regular python program that I created and put it on my site?  Any help appreciated.

---

### Post by jfparis on 2010-02-17
You have several options

Create a simple CGI in python [http://docs.python.org/library/cgi.html](http://docs.python.org/library/cgi.html)

Investigate WSGI: [http://www.wsgi.org/wsgi/](http://www.wsgi.org/wsgi/) (it is a replacement for CGI)

Python provides you with nice frameworks such as django or pylons to create webapps
Both of them run on top of wsgi

---

### Post by ubudog on 2010-02-17
Thank you.  I will look into that.

---

