---
title: "dhcpd + dhcp3"
date: 2009-11-07
forum: Server Platforms
---

### Post by superdave16 on 2009-11-07
So i have one main computer im using its a 1.6 ghz amd sepron with 1 gig, and a 40 gb harddrive and ubuntu 9.10 of course.

i also have a server with 9.10 ubuntu server on it. no gui updates and set up to internet with a usb wireless adapter, i also have one ethernet eth0 which i want to share my connection with my wlan0 usb adapter. the thing is im a bit confused on setting up my dhcp server. I also have a a dlink router inbetween the eth0 and the other computer... ( my xbox 360 with livecd gentoo xenon. which i need internet to install ubuntu to it over debootstrap.) 

Anyone up for brain storming??

---

### Post by Iowan on 2009-11-08
Depending on how big/complex the network will be, give **dnsmasq** a look. For my small (tiny?) network, it ties DHCP and DNS together - clients get DHCP address and can ping other DHCP clients by name... and I can give static leases to servers and network printers.

---

### Post by superdave16 on 2009-11-08
ok ill look into it thanx ill message back if i need some help.

---

