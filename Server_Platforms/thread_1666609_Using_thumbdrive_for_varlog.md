---
title: "Using thumbdrive for /var/log"
date: 2011-01-13
forum: Server Platforms
---

### Post by bennychee on 2011-01-13
Hi all,

  Any one has experience in using a thumbdrive for all /var/log entries? I am trying to reduce write to the harddisk on idle times as I m running RAID 1 and a write entry means 2 harddisk spin-ups.

Benny

---

### Post by sj1410 on 2011-01-14
Yes you can.

format you thumbdrive. copy every thing from /var/log/ to the drive and mount it

```
mount /dev/sdc1 /var/log
```

to make it permanent edit your /etc/fstab

```
/dev/sdc1 /var/log            ext3    relatime        0       2
```

where sdc1 is your thumbdrive

---

### Post by bennychee on 2011-01-14
Cool.

Also, do you see any increase in performance of the box or the life expectancy of the HDD?

Zehn

---

### Post by sj1410 on 2011-01-14
not much

---

