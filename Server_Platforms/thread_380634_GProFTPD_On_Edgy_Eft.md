---
title: "GProFTPD On Edgy Eft"
date: 2007-03-09
forum: Server Platforms
---

### Post by SadisticAffliction on 2007-03-09
I have been using one of my pc's as an FTP server for simple file backup. Configuring it through GProFTPD and am using edgy eft. Had no issues, then installed some updates through the automatic updater, rebooted as it installed a newer kernel. Now, when I try to start my server either through GProFTPD or by running sudo proftpd I get this same message.

> 
 - IPv6 getaddrinfo 'sadistic-desktop' error: No address associated with hostname



Output of ifconfig if needed is:
> 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra0       Link encap:Ethernet  HWaddr 00:16:B6:9B:F7:CE  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fe9b:f7ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:20 dropped:20 overruns:0 carrier:0
          collisions:14 txqueuelen:1000 
          RX bytes:46026 (44.9 KiB)  TX bytes:8531 (8.3 KiB)
          Interrupt:10 Base address:0x8000 



Why the heck is it having IPv6 issues after a reboot when all was fine before??? Also, i'm a bit of a Linux newbie so please bear with me. I haven't been able to find anything regarding this issue so I honestly don't know what to do.

---

### Post by Mr. C. on 2007-03-11
This is indicating that no IP address is being resolved for: sadistic-desktop.

Configure an entry in /etc/hosts as:

192.168.1.140  sadistic-desktop

MrC

---

### Post by clintonthegeek on 2007-05-26
I'm having the same problem, but

127.0.0.1     clinton-desktop

was already in my /etc/hosts file... changing it to 192.168.2.21 (my actual local IP) didn't help... proftpd still outputs:

 * Starting ftp server proftpd
 - IPv6 getaddrinfo 'clinton-desktop' error: No address associated with hostname
   ...done.

Any ideas?

*EDIT:* Nevermind! Searching around, I discovered that you had to add it to the hosts in IPv6 format. For example, here's my entire /etc/hosts file:

127.0.0.1       localhost
127.0.1.1       clinton-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback *clinton-desktop*
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

