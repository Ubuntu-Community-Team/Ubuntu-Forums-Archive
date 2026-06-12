---
title: "problem with configure network on ubuntu server using drac"
date: 2015-06-18
forum: Server Platforms
---

### Post by benny7 on 2015-06-18
hello
i installed ubuntu 14 server on my server using DRAC of dell. 
i got all the info from my server company like ip address, gateway and so on. i have tried to configure the network using DHCP, i have tried static ip with the details i have but no matter what i do i cant seem to make it work. 
when i'm trying to ping 8.8.8.8 i get: connect: Network is unreachable

thanks

---

### Post by TheFu on 2015-06-19
> **benny7 said:**
> hello
i installed ubuntu 14 server on my server using DRAC of dell. 
i got all the info from my server company like ip address, gateway and so on. i have tried to configure the network using DHCP, i have tried static ip with the details i have but no matter what i do i cant seem to make it work. 
when i'm trying to ping 8.8.8.8 i get: connect: Network is unreachable

thanks

Since you only have 1 bean, we have no way to know your level of expertise.
Please post the** /etc/network/interfaces** file and the output from **sudo lshw -C network** and **route** for any help.
It would also be helpful if you provided the exact data provided by your network admin for the static IP/netmask and gateway.

[http://blog.jdpfu.com/2013/08/23/common-answers-for-ubuntu-and-linux-issues](http://blog.jdpfu.com/2013/08/23/common-answers-for-ubuntu-and-linux-issues) has my most common answers to things like this - troubleshooting networking 101 is what you need, methinks.

---

