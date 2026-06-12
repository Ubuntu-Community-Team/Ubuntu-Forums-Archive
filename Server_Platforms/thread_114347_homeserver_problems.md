---
title: "homeserver problems"
date: 2006-01-08
forum: Server Platforms
---

### Post by nbx909 on 2006-01-08
My home server (p3 750mhz 128mb ram ubuntu 5.10) is messed up... HTTP works fine, but the problem is ssh and ftp. They lag. When i connect to ssh it takes forever to connect to it (has never done this before) then after a while it will prompt me for my password then it runs perfectly! FTP is slow it takes forever for a directory to show, but downloads and uploads run at normal speed.
I've switch network cables, network cards, routers, switches, i have no idea what is going on. None of the other computers on my network are having any problems. This randomly showed up yesterday and i've been messing with it since. Also it can't be the OS since i used a live cd and tried it. Any ideas?

ADDED: it also pings great.

---

### Post by ape on 2006-01-08
make sure that your name resolution is working properly between the machines.  If the ssh server is having a problem resolving the client machine's name, it will cause lags.

---

### Post by nbx909 on 2006-01-08
i've tried connection to it from a windows machine using putty and i still get lag to start off with. also how could i check name resultion?

---

### Post by grendelkhan on 2006-01-08
try going to it vi ip address first, then name and see if there is a difference.

---

### Post by spade_shark on 2006-01-12
Is your subnet mask correct?  ie are all LAN PCs set to 255.255.255.0?  Don't use 255.0.0.0.  Make sure all PCs match.

---

### Post by LordHunter317 on 2006-01-12
[QUOTE=nbx909]My home server (p3 750mhz 128mb ram ubuntu 5.10) is messed up... HTTP works fine, but the problem is ssh and ftp. They lag. When i connect to ssh it takes forever to connect to it (has never done this before) then after a while it will prompt me for my password then it runs perfectly! FTP is slow it takes forever for a directory to show, but downloads and uploads run at normal speed.[/quote]Have you setup or configured a firewall?  I suspect a combination of a firewall and name resolution issues, if I had to make a wild guess.

[quote=spade_shark]Is your subnet mask correct? ie are all LAN PCs set to 255.255.255.0? Don't use 255.0.0.0. Make sure all PCs match.[/quote]255.0.0.0 is a perfectly cromulent subnet mask if you're in the right private address range, and have a /8.  And there is one, so this is just poor advice.

---

