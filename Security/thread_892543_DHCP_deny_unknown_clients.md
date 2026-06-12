---
title: "DHCP deny unknown clients"
date: 2008-08-17
forum: Security
---

### Post by Girya on 2008-08-17
Hi, I have a small home network connected to the internet through a linksys "batbox" with a firewall. I've configured a DHCP server to hand out ip addresses to the computers on my network and deny unknown clients. 

Occasionally a deny unknown client message appears in my syslog as below 

  > Aug 16 13:21:07 ubuntuserver dhcpd: DHCPREQUEST for 192.168.1.100 from 00:19:e3:05:fe:68 via eth0: unknown lease 192.168.1.100.
Aug 16 13:21:17 ubuntuserver dhcpd: DHCPDISCOVER from 00:19:e3:05:fe:68 via eth0: unknown client

My question is what do I do to figure out what is going on? 

thanks kevin :confused:

---

### Post by cariboo on 2008-08-17
Which computer does that mac address belong to. To find out what the mac address of your computers are in Ubuntu in a terminal type:

```
ifconfig
```

Which should result in something like this (this is only the first line of the output):

```
eth0      Link encap:Ethernet  HWaddr 00:16:17:9c:84:b5
```

HWaddr is the mac address.

In Windows go to Start-->Run and type cmd and hit enter, in the dos window type:

```
ipconfig /all
```

In the resulting output you will something similar to linux.

Jim

---

