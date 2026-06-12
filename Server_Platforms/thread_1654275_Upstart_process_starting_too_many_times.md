---
title: "Upstart process starting too many times"
date: 2010-12-28
forum: Server Platforms
---

### Post by map7 on 2010-12-28
I'm using ubuntu 10.10 and trying to get hylafax 6.0.5 working under it.  

I've compiled hylafax and all that's left is getting the faxgetty program to start through upstart. The problem is when I use the following it starts 11 processes for some reason.

/etc/init/ttyS0.conf
```
# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /usr/local/sbin/faxgetty -D ttyS0
```

If I comment out the respawn then it will only start once, but then if it dies it will not respawn.  

When there are 11 processes they all fight for the modem and the modem just clicks on and off.  One process if fine. 

How do I set this up with respawning and one process.

---

