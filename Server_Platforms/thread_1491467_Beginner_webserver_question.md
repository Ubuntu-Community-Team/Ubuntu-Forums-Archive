---
title: "Beginner webserver question"
date: 2010-05-23
forum: Server Platforms
---

### Post by spiritofelric on 2010-05-23
I want to test some java applet client/server code.  From a fresh 8.04 Ubuntu setup I try my local ip in a browser ([http://192.168.1.100/](http://192.168.1.100/)), however it doesn't run by default.

Do i need to install a web service application like apache or are there some basic features already in Ubuntu?

-------------------------------------------------------------

I discovered that i do indeed need to setup a webserver.  Sorry for the spam.  Luckily apache is working by default install ^_^ (thank you higher power).

Here's a great vid for php server setup:
[http://www.lullabot.com/videos/install-local-web-server-ubuntu](http://www.lullabot.com/videos/install-local-web-server-ubuntu)

---

### Post by Skidbladniir on 2010-05-24
You need to install apache.

```
aptitude install lamp-server^
```That will install LinuxApacheMysql[and]Php.
So, when you go to 192.168.1.100, you get a webpage.

X_X ... Sorry... Didn't read it all... Wish I could find a delete button...

---

