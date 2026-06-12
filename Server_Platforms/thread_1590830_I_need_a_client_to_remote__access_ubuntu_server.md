---
title: "I need a client to remote  access ubuntu server"
date: 2010-10-08
forum: Server Platforms
---

### Post by hoboy on 2010-10-08
I have installed ubuntu server 10.10 on a pc, I want to access it remotelly, I need some sugestions for a client program, that also had gui interfaces.

---

### Post by Seewolf on 2010-10-08
Depending on your needs, I would look at Webmin:

[http://www.webmin.com/](http://www.webmin.com/)

Some of the modules won't work with the latest version of Ubuntu server but they will catch up eventually.  Otherwise, it is a pretty complete web-interface based server management system.

---

### Post by bcdudley on 2010-10-08
Install openssh-server to your server. Then run putty on your client. You will be able to do everything you need from that.

---

### Post by lisati on 2010-10-08
Depending on what I'm doing, I either use webmin or SSH via "Remote desktop viewer" to access my server.

---

### Post by Seewolf on 2010-10-08
I would agree with lisati.  Webmin is great for a lot of things, but there are things that it can't do and you need a CLI.  I use Putty from Win and the "Remote Desktop Viewer" from Ubuntu.

---

### Post by pricetech on 2010-10-08
Another vote for SSH, but I'll add NX from nomachine dot com.  Client, Node, Server on your Ubuntu box and Client on your laptop.  They have a client for Linux, Windows, Mac, so you're covered whatever your client OS is.

---

