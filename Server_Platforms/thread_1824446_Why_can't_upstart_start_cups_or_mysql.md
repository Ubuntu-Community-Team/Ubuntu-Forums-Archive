---
title: "Why can't upstart start cups or mysql?"
date: 2011-08-13
forum: Server Platforms
---

### Post by CptanPanic on 2011-08-13
For some reason I can't start mysql or cups using upstart i.e. "service cups start" results in "start: Job failed to start".  How can I debug this?  I also tried resintalling using synaptic, but that failed also.  This is with 11.04  

I found some more info in boot.log  

`AppArmor parser error for /etc/apparmor.d/usr.sbin.cupsd in /etc/apparmor.d/tunables/global at line 17: Could not open 'tunables/proc'`

UPDATE: The proc file was missing, so I copied it from backup and everything works now.

---

### Post by CptanPanic on 2011-08-13
Attached is strace of "service cups start"

---

