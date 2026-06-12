---
title: "Trying to get Ubuntu vbox to connect with pfSense vbox"
date: 2012-04-27
forum: Virtualisation
---

### Post by OoBoonTooPerson on 2012-04-27
Here is my setup: Windows 7 host running two Virtualbox machines: pfSense and Ubuntu 10.4

Ubuntu adapter settings: [http://i.imgur.com/lQYXn.png]("http://i.imgur.com/lQYXn.png")

pfSense WAN adapter settings: [http://i.imgur.com/VVSSV.png]("http://i.imgur.com/VVSSV.png")

pfSense LAN adapter settings: [http://i.imgur.com/q8Jrd.png]("http://i.imgur.com/q8Jrd.png")

In pfSense I configured the WAN with DHCP and manually assigned the LAN an IP address.

My question is what do I need to do in Ubuntu to get it to connect to the pfSense router?

---

### Post by newbie-user on 2012-04-27
Did you set Ubuntu to have a static ip also? Ubuntu's static ip should be within the same subnet as the pfsense lan.

---

