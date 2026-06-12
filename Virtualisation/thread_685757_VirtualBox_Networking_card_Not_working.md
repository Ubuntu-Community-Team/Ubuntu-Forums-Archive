---
title: "VirtualBox Networking card Not working"
date: 2008-02-02
forum: Virtualisation
---

### Post by sportman1280 on 2008-02-02
I am trying to get my wireless to work in Virtualbox but not succeeding in anyway.  What do i need to do in order to get this to work?

---

### Post by goldsniper on 2008-02-09
i don't know about wireless in vbox, but for enabling networking in vbox, you can setup a manual config if dhcp not working. 

If you use winxp as guest OS:

click [start] - [control panel]-[network connections]

right click on [Local Area Connection] - choose properties.

scroll down to [Internet Protocol(TCP/IP) - double click that.

enter as follows:

IP address    : 10.0.2.15
Subnet Mask: 255.255.255.0
Default gateway : 10.0.2.2

dns server: 10.0.2.2

hopes this helps

---

