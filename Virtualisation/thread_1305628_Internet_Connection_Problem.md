---
title: "Internet Connection Problem"
date: 2009-10-30
forum: Virtualisation
---

### Post by scott4265 on 2009-10-30
Hey guys, 
I'm running Karmic in Vmware Player on Windows7, and I'm unable to connect to the internet. I'm fairly new to Ubuntu, but I ran Jaunty (just to tinker with) on a dedicated drive with absolutely no net difficulty (on this box). So I'm thinking Vmware is the issue, and I feel like the solution is probably pretty straightforward, but I'm not sure how to go about fixing it. I'm also not certain what information you might need to help, but here are a few things:

Both OS's are 32bit. And Vmware is v. 3.0.0

lspci | grep net:
02:01.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)

cat /etc/network/interfaces:
auto lo
iface lo inet loopback


Happy to provide any other information. 
TYVMIA :D

---

