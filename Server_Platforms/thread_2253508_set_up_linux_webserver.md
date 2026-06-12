---
title: "set up linux webserver"
date: 2014-11-20
forum: Server Platforms
---

### Post by manthos on 2014-11-20
Hallo, i am using linux on my laptop for home use besides dual boot with windows few years now.
In my free time i want to learn how to design my own website and to set up a webserver on my old PC.
Witch linux distro i can use to set up the server and what i need to know from scratch to reach my target?
thanks in advance.

---

### Post by Lars Noodén on 2014-11-20
Any distro will work.  The main difference between them is the choice of default programs including the desktop environment. You can add either nginx or apache2 to yours from the repository via the Software Center or Synaptic.  Apache is the #1 most popular server and, among "active sites" and "busiest" sites, nginx is #2 according to the latest Netcraft survey.  Both are easy to use, there are plenty of directions and guides, but which one would you like to try first and what kind of activities were you planning on trying?  Apache2 is a good default choice.

---

### Post by frankmorris2 on 2014-11-20
Hello,

I would also recommend you take a look at the Ubuntu Server Guide:

[https://help.ubuntu.com/14.04/serverguide/index.html](https://help.ubuntu.com/14.04/serverguide/index.html)

This document contains a lot of interesting topics for server management.

Have a nice day.

---

### Post by irv on 2014-11-20
I have a web server running on a Ubuntu 14.04 server install. Just follow these links.
[http://www.ubuntu.com/download/server/install-ubuntu-server]("http://www.ubuntu.com/download/server/install-ubuntu-server")
Or follow this guide from this PDF file.
[https://help.ubuntu.com/lts/serverguide/serverguide.pdf]("https://help.ubuntu.com/lts/serverguide/serverguide.pdf")
After you have your server installed and running then set up your Apache server with My SQL and PHP.
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Once you have your server up and running you can control your server remotely from anywhere with SSH. To login to your server just use this command from a terminal 
ssh username@servername

---

### Post by LHammonds on 2014-11-20
FYI - You don't have to dual-boot to test/learn Linux.  You can install Oracle VirtualBox in Windows and run Linux in a virtual.  Its a great learning environment because you can create "snapshots" at various stages and quickly/easily rollback to a prior step if things did not work out right or if you just to try it different ways.

I am in the process of updating my 12.04 tutorials to 14.04 but the "How to Setup Ubuntu Server" is mostly done and in my sig.

LHammonds

---

### Post by mastablasta on 2014-11-21
> **LHammonds said:**
> FYI - You don't have to dual-boot to test/learn Linux.  You can install Oracle VirtualBox in Windows and run Linux in a virtual.  Its a great learning environment because you can create "snapshots" at various stages and quickly/easily rollback to a prior step if things did not work out right or if you just to try it different ways.


I would add that there are readily available images for this as well. have a look at bitnami stack or turnkey Linux. there is no installing needed. you just load the image set the IP and then connect to it form browser.

ofcourse you can also install your own server. it's to that difficult. ubuntu server is easy enough. if oyu have a separate computer as server then you might want to add some graphical interface to control server via web browser. I use Ajenti, but Zentyal is also good. some use webmin, but I don't think it is supported.

---

