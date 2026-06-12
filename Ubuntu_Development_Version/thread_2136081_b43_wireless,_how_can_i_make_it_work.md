---
title: "b43 wireless, how can i make it work"
date: 2013-04-16
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2013-04-16
I installed 13.04 and get no wireless. I get an error on boot something about b43 etc...

i tried running this after looking on the web but it is not locatable

> dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ lspci -vvnn | grep 14e4

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ sudo apt-get install firmware-b43-installer
[sudo] password for dv9000: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer
d

---

### Post by sdowney717 on 2013-04-16
fixed with this here

So why cant it just work, cause its non-free?
So how much does it cost to make it work for ubuntu?
> If it is a BCM4311 these should take care of it ( do with an ethernet connection)

sudo apt-get remove --purge bcmwl-kernel-source 
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43

---

