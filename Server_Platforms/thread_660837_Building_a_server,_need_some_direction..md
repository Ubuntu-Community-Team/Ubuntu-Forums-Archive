---
title: "Building a server, need some direction."
date: 2008-01-07
forum: Server Platforms
---

### Post by amd is the best on 2008-01-07
Hello everyone, I am in need of some direction/pointers.  I want to help out my fathers small business by building/configureing a server for their very small network (4 windows xp based pc's).  I would like the server to be a PDC, file and print serving, and act as their DSL router and maybe an FTP and HTTP server in the future.  If anyone can point me in the right direction on where to start I would greatly appreciate any/all help!

I have just installed a clean copy of Ubuntu 7.10 Server.

Thank you all in advance!

Nick

---

### Post by metoor30 on 2008-01-07
You can use Samba for their PDC, print and file server needs.  

You can route using iptables.

I would try searching on each topic in the forums for a HowTo.

---

### Post by hkgonra on 2008-01-07
You might want to look at SME server [http://wiki.contribs.org/Main_Page](http://wiki.contribs.org/Main_Page)
It is made to be a small business server with everything ready from the beginning.

---

### Post by rickyjones on 2008-01-07
> **amd is the best said:**
> Hello everyone, I am in need of some direction/pointers.  I want to help out my fathers small business by building/configureing a server for their very small network (4 windows xp based pc's).  I would like the server to be a PDC, file and print serving, and act as their DSL router and maybe an FTP and HTTP server in the future.  If anyone can point me in the right direction on where to start I would greatly appreciate any/all help!

I have just installed a clean copy of Ubuntu 7.10 Server.

Thank you all in advance!

Nick

Hi,

I highly recommend that you purchase an actual DSL router for the internet connection. It is always better to segregate tasks when it comes to machines.

As for configuring the server to be a web host, samba, PDC, etc, I know that there are several tutorials on the forums and on [www.howtoforge.com](www.howtoforge.com) that may be of some use to you.

For example: [http://howtoforge.com/ubuntu-gutsy-samba-domaincontroller](http://howtoforge.com/ubuntu-gutsy-samba-domaincontroller)

-Richard

---

