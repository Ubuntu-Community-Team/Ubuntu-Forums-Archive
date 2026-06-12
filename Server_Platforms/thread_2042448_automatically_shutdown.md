---
title: "automatically shutdown"
date: 2012-08-14
forum: Server Platforms
---

### Post by pininy on 2012-08-14
Hi,

Just upgraded my server from 9.04 to 12.04 LTS, not the first machine i have done.

but this time the only difference is i have raid 5 array configured on my HP server.

there are no kernel panic, and i grep for halt, boot.. nothing came up. it seems to have shutdown after non-activity.. :-(

anyone can help ? what to check?

many thanks!

---

### Post by pininy on 2012-08-14
hi,

did a last -x 

homas@corp-nms-01:/var/log$ last -x
thomas   pts/2        sinlt168w.corp.s Wed Aug 15 00:56   still logged in
thomas   pts/0        ubuntu-dev.corp. Wed Aug 15 00:52   still logged in
runlevel (to lvl 2)   3.2.0-29-generic Wed Aug 15 00:49 - 01:02  (00:13)
reboot   system boot  3.2.0-29-generic Wed Aug 15 00:49 - 01:02  (00:13)
thomas   pts/4        57.4.53.6        Tue Aug 14 12:33 - crash  (12:15)
thomas   pts/3        ubuntu-dev.corp. Tue Aug 14 12:20 - crash  (12:29)
thomas   pts/3        ubuntu-dev.corp. Tue Aug 14 12:19 - 12:19  (00:00)
thomas   pts/2        ubuntu-dev.corp. Tue Aug 14 10:20 - crash  (14:28)
thomas   pts/1        ubuntu-dev.corp. Tue Aug 14 10:19 - crash  (14:30

---

### Post by CharlesA on 2012-08-15
Anything in the syslog or dmesg?

---

### Post by pininy on 2012-08-16
> **CharlesA said:**
> Anything in the syslog or dmesg?

the strange thing is there is none, just completed a 2 hour memtest and found no errors.

is there anything else that i can check? for

---

### Post by LHammonds on 2012-08-16
Make sure your partitions are not full...especially your root

```
df -h
```

---

