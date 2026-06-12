---
title: "Setting Up a VPN"
date: 2007-05-14
forum: Server Platforms
---

### Post by Cbeck527 on 2007-05-14
Hi all, I have been using Ubuntu since 6.06, and I recently upgraded to 7.04. I have a server running 6.06 server apache, and a ftp server. ([www.chrisbecker.info](www.chrisbecker.info)) Anyway, what I wanted to eventually do would be setting up a VPN. My Highschool has one, and on a windows box it is extremely simple to connect. I am interested in setting up a VPN so that I can connect to my home network from the internet. 
Is this possible to do this with my Ubuntu server?
Also, are there any specific hardware requirements? IIRC, I think two ethernet cards are required.

Thanks in advance for all your help.
--Cbeck

---

### Post by seamless on 2007-05-15
Two ethernet cards are not required. It is possible. OpenVPN would be your best best [http://openvpn.net/]("http://openvpn.net/") has full documentation on setting up the client and server.

---

### Post by Frosty Cold Drink on 2007-05-15
Its a bit advanced, but it may be worth it to set up L2TP+IPSec. Recent Windows and Mac clients would be able to connect without installing additional software.

[http://www.jacco2.dds.nl/networking/index.html](http://www.jacco2.dds.nl/networking/index.html)

---

### Post by Cbeck527 on 2007-05-15
Thanks for the quick responses! I think that I am going to try Frosty Cold Drink's method because I would rather not have to install additional software.

Cheers.

---

