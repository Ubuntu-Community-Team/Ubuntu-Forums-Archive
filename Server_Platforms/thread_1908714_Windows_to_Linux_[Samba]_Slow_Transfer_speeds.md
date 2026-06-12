---
title: "Windows to Linux [Samba] Slow Transfer speeds"
date: 2012-01-13
forum: Server Platforms
---

### Post by Aaron053191 on 2012-01-13
Basically the topic says it all, but I will list some details.

I am transferring files from Windows PC to my Ubuntu Home Server.

My Server is connected to the router via Lan.

I am transferring files from my Windows PC over wireless, through router, and into the server via Lan.

I am receiving transfer speeds of 700-900 KB/s.

Any ideas? Help appreciated.

Thanks! :p

---

### Post by Cheesemill on 2012-01-14
How fast is your wireless?
That could be your bottleneck.

---

### Post by ian dobson on 2012-01-14
Hi,

What does your /etc/samba/smb.conf look like.

On my 5GHz wireless network I'm getting between 7-11Mbyte/sec write from my Windows7 box to my Ubuntu server.

I manually configured samba for maximum performance.

Here's part of my global section of my smb.conf:-
```

[global]
read raw = yes
write raw = yes
wide links=yes
getwd cache=yes
stat cache = yes
strict sync = no
use sendfile = yes
large readwrite = yes
oplock contention limit = 5
oplock break wait time = 100
case sensitive = true
strict allocate = yes
max xmit = 131072
use sendfile = Yes
dead time = 15
getwd cache = Yes

disable netbios = yes
nmbd bind explicit broadcast = no
netbios name = alpha2

min receivefile size = 43638
aio read size = 643638
aio write size = 643638
aio write behind = false

##Optimize tcp
socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 IPTOS_LOWDELAY SO_KEEPALIVE

write cache size = 12826144
strict allocate = yes

```

the socket options and aio options make to biggest difference for performance.

Regards
Ian Dobson

---

