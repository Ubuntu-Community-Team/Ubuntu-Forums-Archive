---
title: "dns settings for my rpi at osmc/kodi"
date: 2018-08-07
forum: Ubuntu/Debian BASED
---

### Post by marchello_lippi2 on 2018-08-07
Hi all, 
How do I set specific dns settings for my rpi at osmc/kodi (debian-based) ? 
```
$ uname -a
Linux osmc 4.14.34-2-osmc #1 SMP PREEMPT Thu Jun 7 18:43:25 UTC 2018 armv7l GNU/Linux
```
Tried to modify /etc/resolv.conf and it worked for me till reboot, but then my modifications were erased. 
The device gets settings from dhcp server. 
Please advise.

Upd: in the meantime I've created my own resolv.conf version in the home directory and created crontab record to copy it instead of original one each hour (ugly, but works)
```
0 * * * * cp /home/osmc/resolv.conf /etc/resolv.conf
```

---

### Post by TheFu on 2018-08-07
osmc networking isn't normal debian. They use conman.
No /etc/network/interfaces file is used.
No /etc/netplan/

I'd suggest asking this question on  the OSMC forums, if you can't find the answer.  The main packager is very active and the core 10 forum users there are expert at this stuff.

---

