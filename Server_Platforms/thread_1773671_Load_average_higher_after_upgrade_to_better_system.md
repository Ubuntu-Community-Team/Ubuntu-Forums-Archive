---
title: "Load average higher after upgrade to better system -hmmmm?"
date: 2011-06-02
forum: Server Platforms
---

### Post by kenanderson on 2011-06-02
Greetings,
I used to run on a slow dual-core server with non-raid disks.

I upgraded to a quad-core server running at a faster speed, along with a RAID-1 config (mirroring).

Both the old and new servers run exactly the same software. 

With a given/same input load, the old server had a load average of 0.50.

The new server, with the same input run as 1.25 load average.

Stumped. Thoughts or suggestions?

thx in advance
ken

---

### Post by ruffEdgz on 2011-06-03
Does this still happen? When you do the command 'top' and sort by %CPU or %MEM, do any services pop out as using to much of one or the other.

Also, when you say the load average is 1.25, was it on the 1, 5, or 15 minute section when (1min,5min,15min):
```
uptime | awk '{print $10 $11 $12}'
```

---

