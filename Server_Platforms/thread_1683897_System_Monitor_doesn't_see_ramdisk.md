---
title: "System Monitor doesn't see ramdisk"
date: 2011-02-08
forum: Server Platforms
---

### Post by YesWeCan on 2011-02-08
I'm using 10.04.1 64-bit server. In the course of testing my system RAM I created and mounted a 5GB ramdisk:
```
mount -t tmpfs -o size=5000M tmpfs /tmp/ramdisk/
```

I was watching the System Monitor resources tab as I did this (the live graph). Before, the RAM usage was about 2GB (out of 8GB available). It did not change when I created the ramdisk nor when I filled it to the brim with files.

The correct RAM usage is shown by 'free -m'
The ramdisk is listed by 'mount'

The ramdisk is not shown in the filesystem tab of System Monitor either.


Is this a "feature" or an omission, or did I screw up?

---

