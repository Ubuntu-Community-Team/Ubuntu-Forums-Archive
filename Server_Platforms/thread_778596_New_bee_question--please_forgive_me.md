---
title: "New bee question--please forgive me"
date: 2008-05-02
forum: Server Platforms
---

### Post by hoboy on 2008-05-02
I am looking at ubuntu server machines, you have the picture of some hardware machines on the site [http://www.ubuntu.com/](http://www.ubuntu.com/), what type of machines are they ? what are they called ? how can i get them ? because I need to use ubunut server edition, but I don't know anything about it,specially not the hardwares it will run on, do I have to have the hardware pictured on the your site ? to use ubuntu server edition ? can I install ubuntu server edition on my pc ?
or do I need the machine that have picture on the site ?

---

### Post by Cadmus on 2008-05-02
Ubuntu is not limited to any specific hardware, and will run well on nealy all sevrers, the only thing that springs to mind to look at are the compatibility of storage controllers (RAID cards).

---

### Post by mozetti on 2008-05-02
> **hoboy said:**
> can I install ubuntu server edition on my pc ?
or do I need the machine that have picture on the site ?

Yes, you can install the server edition on your PC. The server edition doesn't come with a GUI installed, but it's easy to add one. You should use the server edition if you want to use your PC as a server: file server, webserver, etc. Otherwise, just use the desktop version.

---

### Post by az on 2008-05-02
> **hoboy said:**
> 
or do I need the machine that have picture on the site ?

The server editio will run on any PC.  As well, the server software will run fine on any PC that is running the Desktop version.  The server packages do not interfere with the desktop software and vice versa.

The only thing with the server installation is that it will install a kernel that is optimized for server hardware.  If this causes you problems (like with some desktop hardware such as some multimedia keyboards and the like, you can simply install the generic kernel (the one that you get when you install the desktop version).

sudo apt-get install linux-generic

---

