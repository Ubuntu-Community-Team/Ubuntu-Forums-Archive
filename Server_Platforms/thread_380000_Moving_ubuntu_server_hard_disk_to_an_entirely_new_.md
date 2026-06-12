---
title: "Moving ubuntu server hard disk to an entirely new server"
date: 2007-03-09
forum: Server Platforms
---

### Post by murattas on 2007-03-09
Hi,

I have moved the ubuntu server IDE disk from an IBM server to a Dell PC..The second PC successfully booted and mounted the partitions and started the LAMP servers with no problem. 

But I have problems with the ethernet card. When I set the IP adress it says:
[B]SIOCSIFADDR:No such device
eth0:Error while getting interface flags:no such device
SIOCSIFNETMASK: No such device [/B]

Dmesg output:

[B]# grep eth0 dmesg
e1000:eth0:e1000_probe:Intel(R) PRO.......[/B]

This topic is urgent.Please reply it as soon as possible..

Thanks...

---

### Post by MJN on 2007-03-09
What's the output of ifconfig?
 
It could well be that eth0 (which is just a label) is still being reserved for your 'old' network card... Hence, have a look in /etc/iftab and check to see if the MAC address listed against eth0 is for your old card. If it is then try changing it to match the MAC address of your new one...
 
Mathew

---

