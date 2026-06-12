---
title: "WinXP work pc logging in my ubuntu pc?"
date: 2009-12-08
forum: The Cafe
---

### Post by brookie on 2009-12-08
Hi all, 

I'm working from home today and noticed that my Ubuntu Karmic syslog fills up with this when I plug my work pc running WinXP into my wireless router. 

ec  8 10:42:11 (my pc name) kernel: [10225.323463] [UFW BLOCK] IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:12:f0:70:25:01:08:00 SRC=192.168.1.144 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=1835 PROTO=UDP SPT=137 DPT=137 LEN=58 

I usually have DHCP turned off on my router and use static ips on all my home ubuntu pcs. I had to turn on DHCP to get the work pc online. I do not have admin privs to give it a static ip. The work pc is the .144 machine.

Any clues?  :confused:
Cheers,
brook

---

### Post by LowSky on 2009-12-08
Do you use Samba for networking? i could be the Windows PC trying to establish a network. Especially if its a Work computer that normally has access to network drives.

---

### Post by brookie on 2009-12-08
I don't have samba up and running now. I did on my Intrepid machine but haven't gotten around to it since I went to Karmic. 

You are probably right! I should have thought of that, the bugger (network neighborhood or something) is probably trying to network with my ubuntu pc. 

Thanks!

---

