---
title: "Win32 box issuing strange DNS queries"
date: 2010-11-26
forum: Security
---

### Post by WinstonChurchill on 2010-11-26
An older windows box (running XP) on my LAN repeatedly makes a DNS query for the address "q0jb.____PPC____ __________________.", beginning about 15 minutes after it is turned on. My DNS server dutifully responds with an "NXDOMAIN", but the Win32 box continues to make this query, about 4 times a second, until it is shut down.

Is this some windows quirk I'm not familiar with? Or is it time to nuke the Windoze box? It's the last one I've got not running some UNIX-variant...

Here's a tcpdump of the query (layer2+ headers included):
```

23:19:23.804500 IP (tos 0x0, ttl 128, id 34188, offset 0, flags [none], proto UDP (17), length 81)
    10.0.0.101.63860 > 10.0.0.1.53: [udp sum ok] 35330+ A? q0jb.____PPC____ __________________. (53)
    0x0000:  001b 215e 8810 00e0 4d1f e182 0800 4500  ..!^....M.....E.
    0x0010:  0051 858c 0000 8011 a0aa 0a00 0065 0a00  .Q...........e..
    0x0020:  0001 f974 0035 003d 621f 8a02 0100 0001  ...t.5.=b.......
    0x0030:  0000 0000 0000 0471 306a 621e 5f5f 5f5f  .......q0jb.____
    0x0040:  5050 435f 5f5f 5f20 5f5f 5f5f 5f5f 5f5f  PPC____.________
    0x0050:  5f5f 5f5f 5f5f 5f5f 5f5f 0000 0100 01    __________.....

```

---

### Post by Kinstonian on 2010-11-26
Sometimes protocol analyzers will misinterpret packets, but looking at the hex and what tcpdump shows, everything looks correct.  Why you're getting those packets, I don't know.

I would think it would be more likely due to something like buggy software than an attack.  If it is an attack there will certainly be more evidence of it other than odd DNS queries to your DNS server, so you may want to look for more conclusive evidence on the host.

---

### Post by WinstonChurchill on 2010-11-27
> **Kinstonian said:**
> /you may want to look for more conclusive evidence on the host.
There is not enough tequila in the world to sustain me through searching for Windows viruses... I was just hoping this was some NetBIOS quirk I was unaware of...

**EDIT: **For anybody that comes across the same problem, killing one of the svchost.exe processes seems to stop it, but the I/O seems to be coming from lsass.exe.

---

