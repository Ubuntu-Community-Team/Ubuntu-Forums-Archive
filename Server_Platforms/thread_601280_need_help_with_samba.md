---
title: "need help with samba"
date: 2007-11-03
forum: Server Platforms
---

### Post by crazyone on 2007-11-03
hi i did a quick search for this so sorry if this has been solved before. my problem is sense i have been using my server on my smoothwall router through a dmz pinhole i havent been able to get  to my samba server. i am thinking it has to deal with the fact i have the orange network set to 192.168.1.1 and the green network set to 192.168.0.1. is there away for me to access samba over that. thanks for the help in advance. btw before i had the router on the dmz pinhole i was able to get to the samba server. i would just move it back but it is also my webserver and ftp server so i kinda need to use the dmz pinhole.

---

### Post by HermanAB on 2007-11-03
So, what ports do you have open?  You need at least port 445/TCP for samba.

---

