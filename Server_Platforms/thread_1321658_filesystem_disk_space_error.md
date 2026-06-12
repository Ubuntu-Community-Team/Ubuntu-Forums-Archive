---
title: "filesystem disk space error"
date: 2009-11-10
forum: Server Platforms
---

### Post by junke1990 on 2009-11-10
Hey guys, I'm running a little debian server on a Sheevaplug. It runs of my SD card and has been working properly for months now. Last night logwatch didn't mail me and I was missing my mount's.

I found out my / partition is full but I can't find out why...

```
debian:/etc# du -h --max-depth=0 / -x
1.4G    /
debian:/etc# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mmcblk0p1        2.8G  2.6G   56M  98% /

```

---

### Post by junke1990 on 2009-11-10
hmm a reboot fixed it, strange because it went from 56% too 98% / 100%, I had an uptime of 51 days

---

### Post by Zeosa on 2009-11-10
My guess is you had stuff in /tmp that was purged after the reboot.

---

### Post by junke1990 on 2009-11-10
I didn't, I cleaned it out to 12KB. I ran appt-get autoclean and autoremove.

but even if it was in tmp shouldn't it show up if you ask for the diskspace of / ?

---

