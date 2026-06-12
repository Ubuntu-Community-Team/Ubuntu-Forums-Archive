---
title: "communicate my ubuntu with my guest OS via qemu"
date: 2007-11-27
forum: Virtualisation
---

### Post by herbert tamayo on 2007-11-27
hi, my host OS is ubuntu 7.04 I installed FreeBSD and WinXP using QEMU, so I need your help to do the next:

1. I need that the guest OSs -FreeBSD and WinXP- can do ping to Ubuntu and viceversa, the NIC that qemu use is a realtek 8029, so what I have to do to the 3 of them can communicate between them? for example using ping 

2. If I bring up apache in FreeBSD, can Ubuntu log to that virtual server?

thanks a lot

---

### Post by ruibernardo on 2007-11-27
Hi herbert,

take a look at this page: [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo). In the  Networking section you have the user mode networking and two more options.

"TAP networking" should work if you have a router and "VDE and Dnsmasq" should work if you don't have a router (with a modem/cable-modem or you aren't even connected).

I never really understood the way that user mode networking works, but it is explained on the webpage, try it. If it doesn't, then try one of the other options. They are more *complicated* to set up, but the "virtual" networking (iptables, network interfaces and all the rest) will be more clear and realistic, imo.

Hope this gets you started.

---

