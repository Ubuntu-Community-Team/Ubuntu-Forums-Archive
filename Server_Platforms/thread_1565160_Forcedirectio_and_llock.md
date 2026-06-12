---
title: "Forcedirectio and llock"
date: 2010-08-31
forum: Server Platforms
---

### Post by Mauler5858 on 2010-08-31
I need to mount to a NFS share on a netapp device.  I can mount to it, but without two of our options that our Sun UNIX boxes can: forcedirectio and llock.  This is a Ubuntu 64-bit server platform.

```
servername:/sharename /admin nfs                 rw,bg,hard,intr,proto=tcp,vers=3,rsize=32768,wsize=
32768,forcedirectio,llock 0 0
```

---

### Post by craigp84 on 2010-08-31
Hi,

On Linux there is no forcedirectio option, use actimeo=0 to get the same behaviour (no caching).

There isn't an equivelant to local locks option in Linux. I guess depending on what the data is you could run with the nolock option for the same performance benefit as llock.

---

### Post by Mauler5858 on 2010-08-31
Thanks, I will check this out tomorrow when i get to work.

---

