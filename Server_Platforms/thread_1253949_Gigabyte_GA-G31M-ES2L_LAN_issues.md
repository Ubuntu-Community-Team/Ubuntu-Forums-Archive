---
title: "Gigabyte GA-G31M-ES2L LAN issues"
date: 2009-08-30
forum: Server Platforms
---

### Post by sauce345 on 2009-08-30
So I picked up one of these to use (Gigabyte GA-G31M-ES2) as a light use file server.  Installed Ubuntu 9.04 64 bit on it fine.  The problem seems to be that the Ethernet does not work at all.  When typing the 'lspci' command it tells me that the Ethernet is some Asternok brand or something.  Other threads that I found talking about the GA-G31M-S2L talk about how to blacklist the realtek driver and installing a new one.  However I don't think that this board has the realtek Ethernet and has this other brand Asternok or something a long those lines.

Has anybody else expierenced this with this board?  I would like to get the gig ethernet to work properly.  If can't figure out I suppose will be shipping back since gig ethernet is a deal breaker.

Thanks in advance.

---

### Post by mocka on 2009-09-13
I started using the same board a couple of months ago. It is set up with Ubuntu Server x64. Eventhough my LAN connection is working, I experience slow speeds when it is uploading to another computer. The strange thing is that it works at gibabit speeds when downloading. 

Try to upgrade to the latest stable bios (F8). I wonder if there is any drivers to be found for the card for Linux operating systems.

---

### Post by condemetrius on 2009-11-13
I installed a Gigabyte GA-G31M-ES2L and so ethernet stopped working in Karmic. Actually, another computer in the lan recieved an IP from my dnsmasq and even pings me, but I cannot ping him back, etc. The internet (second eth, static ip) is totally off.

---

