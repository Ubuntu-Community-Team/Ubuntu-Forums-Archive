---
title: "Mounted hard disk Failover?"
date: 2010-11-01
forum: Server Platforms
---

### Post by syth on 2010-11-01
I have an external USB hard disk that I use for backups.  Twice the device has gone offline.  When that happend the root filesystem still retains the directory structure without the disk being present. 

If the backup runs during that time it will completely fill the root filesystem.

Is there a way to make the mounted directory unavailable if it becomes disconnected/unmounted unexpectedly?

Thanks in advance.

Syth

---

### Post by amac777 on 2010-11-01
What program (or command(s)) are you using to make your backups?

---

