---
title: "Host website on ubuntu server 12.04"
date: 2012-07-13
forum: Server Platforms
---

### Post by spleen387 on 2012-07-13
I just installed Ubuntu server 12.04 and I'm completely lost, I've never really used Ubuntu, can someone please help me set it up to host a website?:guitar:

---

### Post by papibe on 2012-07-13
Hi spleen387. Welcome to the forums!

There are several options, but the most common is to install a app combo called LAMP (for Linux Apache MySQL PHP).

Here's a [guide]("https://help.ubuntu.com/community/ApacheMySQLPHP") to get you started.

I hope that helps. Come here often and have fun.
Regards.

---

### Post by wyliecoyoteuk on 2012-07-13
It is also useful to install SSH server using tasksel.
Then you can log in from another pc on the network using: 

ssh username@PCIPaddress

e.g. user1@192.168.0.10

However, if you are really new to Linux you need to learn the command line or use a desktop distro, as Ubuntu server does not by default have a GUI.

One application that can help is webmin

[http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-11-04-natty-server.html](http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-11-04-natty-server.html)

(I would use nano, not vi, change the line:
 sudo vi /etc/apt/sources.list
to
 sudo nano /etc/apt/sources.list)

---

