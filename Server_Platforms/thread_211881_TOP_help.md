---
title: "TOP help"
date: 2006-07-09
forum: Server Platforms
---

### Post by peanut butter on 2006-07-09
hi i need some help interpriting this top output:

```

top - 04:58:34 up 10 days, 21:02,  1 user,  load average: 0.07, 0.05, 0.01
Mem:   3623540k total,  3601912k used,    21628k free,    83824k buffers
Swap:  8193140k total,   645636k used,  7547504k free,  2131260k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    1 root      16   0  1480  512 1320 S  0.0  0.0   0:04.31 init
 5959 root      16   0  4684 1572 4252 S  0.0  0.0   0:01.82 sshd
 5605 syslog    16   0  1692  672 1508 S  0.0  0.0   0:01.43 syslogd
 5933 root      16   0  4580 1228 4368 S  0.0  0.0   0:00.57 master
24309 root      16   0 13320 3360  11m S  0.0  0.1   0:00.29 apache2
 6064 root      16   0  9068 2048 4892 S  0.0  0.1   0:00.27 miniserv.pl
 6011 nobody    16   0  4576 1664 3880 S  0.0  0.0   0:00.13 proftpd
24312 www-data  15   0 15036 3832  11m S  0.0  0.1   0:00.06 apache2
24311 www-data  15   0 14992 3932  11m S  0.0  0.1   0:00.05 apache2
20460 root      16   0  2132 1064 1844 R  0.3  0.0   0:00.05 top
24316 www-data  15   0 14924 4216  11m S  0.0  0.1   0:00.04 apache2
20400 root      16   0  7468 2656 6964 R  0.0  0.1   0:00.04 sshd
 5945 postfix   16   0  4624 1176 4412 S  0.0  0.0   0:00.03 qmgr
31861 postfix   16   0  4644 1396 4428 S  0.0  0.0   0:00.03 tlsmgr
 5771 mysql     17   0 43648 1688 8748 S  0.0  0.0   0:00.02 mysqld
24466 www-data  15   0 13460 3728  11m S  0.0  0.1   0:00.01 apache2
 5631 root      25   0  1596  404 1424 S  0.0  0.0   0:00.00 dd
 5633 klog      25   0  1484  400 1312 S  0.0  0.0   0:00.00 klogd
 5642 dnsmasq   21   0  1744  596 1572 S  0.0  0.0   0:00.00 dnsmasq

```
it says im useing most of my memory but it also says none of the running processes are useing any memory.:confused:

---

### Post by bikeboy on 2006-07-09
It's not actually using all that memory. I've seen some good explanations but I can't recall them well enough to repeat to you. Have a look here [http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

To see which programs are taking the most ram, try pressing "shift + >" which will sort on the column to the right of the default. "Shift + <" goes the other way. "Shift + R" reverses the column. I also believe the RES column is the most accurate depiction of the physical ram a particular program is using.

Also try running "free" and looking at the "-/+ buffers/cache:" row for ram usage.

Hope that helps you out.

---

