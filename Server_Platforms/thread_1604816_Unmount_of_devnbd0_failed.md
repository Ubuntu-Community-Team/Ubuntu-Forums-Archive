---
title: "Unmount of /dev/nbd0 failed"
date: 2010-10-24
forum: Server Platforms
---

### Post by DrJohn999 on 2010-10-24
After in-place upgrade from 9.10 to 10.04, the message
```
Unmount of /dev/nbd0 failed
``` appears on the console at shutdown, with a warning that data may be lost, and followed by a 10 second countdown, after which shutdown continues normally.
Syslog shows this one line at each boot:
```
Oct 23 10:04:16 m2a74am kernel: [    1.203334] nbd: registered device at major 43
```
Nothing gets mounted explicitly at /dev/nbd0, so I am puzzled about the error message on shutdown.

---

### Post by naptastic on 2011-01-29
*bump*

I'm having the same issue. It's not causing any problems as far as I can see, but it slows down my shutdown by another 10+ seconds.

Perhaps some shutdown script simply needs to check if something is mounted before unmounting it so it can avoid freaking people out?

---

