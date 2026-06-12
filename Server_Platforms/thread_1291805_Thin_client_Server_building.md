---
title: "Thin client Server building"
date: 2009-10-15
forum: Server Platforms
---

### Post by yawasare on 2009-10-15
to you all, am building a thin client server for an school in Ghana, West Africa. the issues am not familar with ubuntu environment, i need help to build  the server and cilents, how to configure them, the systems is going to be built in Canada and am sending them january 2010 so any help will be appreciated, i will have 15 client connect and 1 server, or should go with windows?[EMAIL="ghanacomputer@rogers.com"]Please You Email Me[/EMAIL]

---

### Post by bluntknife on 2009-10-15
Hi,

If the workstations can have an operating system installed on them take a look at trialing ULTEO.  The packages required are included in the Ubuntu repos.
Ulteo will allow you to publish a standard desktop along with applications.

[http://www.ulteo.com/home/en/ovdi/openvirtualdesktop/downloadnow?autolang=en](http://www.ulteo.com/home/en/ovdi/openvirtualdesktop/downloadnow?autolang=en)

Otherwise, if you have PXE enabled workstations with a low amount of RAM take a look at SLAX.  You can configure Slax 'server' (or master) to boot into PXE server mode.  This allows other machines on the network to PXE boot-over-LAN reading all the information they require from the master Slax 'server'.

[http://www.slax.org/](http://www.slax.org/)

Hope this is of some help.

---

### Post by AlexanderDGreat on 2009-10-16
If you're not familiar with Ubuntu environment it may take a while for you to do this. Just go with Windows if you're in a hurry, but that depends on your budget. You can also hire an Ubuntu expert. I use a 1 server 5 Intel Atom setup for my LTSP. LTSP is a complex system, although I've only been using Ubuntu for 5 months, I've been able to set it up because of my previous experience with Windows Servers and basic Network Setups. Good Luck. For your starting reference: [https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by police512 on 2009-10-20
hey,

Opensuse does a good server for LTSP try that!!! i did and its sick

---

