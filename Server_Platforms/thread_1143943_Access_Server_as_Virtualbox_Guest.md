---
title: "Access Server as Virtualbox Guest"
date: 2009-04-30
forum: Server Platforms
---

### Post by MilkeySUFC on 2009-04-30
Hi,

I'm a web developer and, although pretty okay with my development skills, I'm quite lacking in the hardware/admin side.

I have a project I want to start working on that I can have a development machine (a Ubuntu 9.04 laptop) running a Ubuntu 9.04 server (LAMP) as a guest in Virtualbox (so I don't have to have the whole server environment loaded on the development environment).

I'd like to know how to set up the Virtualbox guest session so that I can see the Apache server from the host laptop even (especially) when the laptop is not plugged in to any network.

Thanks,
Milkey

---

### Post by richard42 on 2009-04-30
There's a program VBoxManage that you can run on the host to forward the ports on the host to the development machine.  Although [this description]("http://sk.c-wd.net/wp/2008/01/05/virtualbox-port-forwarding-with-linux-host/") is forwarding SSH, you could do the same for http traffic.  Just forward port 80 instead of port 22.

---

