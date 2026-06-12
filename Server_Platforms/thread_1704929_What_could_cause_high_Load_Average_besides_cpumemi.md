---
title: "What could cause high Load Average besides cpu/mem/iowait?"
date: 2011-03-11
forum: Server Platforms
---

### Post by samosamo on 2011-03-11
I have some "development" Ubuntu Server 10.04 guests virtualized under ESXi 4.1 that sit idle all day until I decide to play with them.  Some of them (about 10 out of 20) experience persistent spikes in Load Average at random times throughout the day and night.  I get notified via Nagios when the event starts, so I quickly jump on an ssh terminal to troubleshoot.  I see the load average is obviously high (>1.0) but there is ZERO activity on the server.  It is very creepy.  CPU is 100% idle, iowait is absolutely zero, plenty of memory is free and none of it is swapped. Even creepier, listing processes shows they are ALL in sleeping state (S).

Any ideas? My next step before going to the ESXi forums is install another Linux flavor, and see if it is affected as well.

---

### Post by samosamo on 2011-03-13
Anyone?

---

