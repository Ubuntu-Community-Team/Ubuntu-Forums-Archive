---
title: "Quake 3 Server high ping on LAN"
date: 2011-01-15
forum: Server Platforms
---

### Post by rage_311 on 2011-01-15
Hey everyone,

This is probably not an Ubuntu-specific issue that I'm having, but I am running Ubuntu 10.04 32-bit server.  I'm running a Quake 3 Arena server and I have unusually high pings (usually around 40-45 ms) when connecting a client on the LAN.  For friends connecting over the Internet in the same state on the same ISP about 20 miles away, pings are even higher than that -- usually about 60+ ms.  Now, I know that's not a terrible ping, but every little bit helps, especially in a first person shooter.  Clearly there's something that's not quite right here.  I can ping the server's internal IP address, in my LAN from a command prompt on my Windows 7 machine, and I consistently get responses of <1 ms, so I know there's not a network setup issue.  I am also simultaneously running a Rune (Halls of Valhalla) server where I get in-game pings of 17-20ms on LAN.

As far as my hardware goes, I'm on a Pentium 4 2.6 ghz with 1.5 GB of RAM.  When I run top, it says that my CPU usage is <5% and I have about 1.2 GB of RAM available.  I'm using a PCI NIC, if that would make any difference.

Also, if I run a non-dedicated Quake 3 server on another Windows 7 machine on the LAN, I average about 5-10 ms ping.

Any ideas on what I could do to troubleshoot this?  It does seem to be Quake-Linux-specific, so I may be at the mercy of somebody who has run a Quake 3 server on a Linux box before.  I've messed with the sv_maxRate setting a bit with no real luck.  Any ideas?  It would be great to get this working smoothly!

Thanks in advance.

---

