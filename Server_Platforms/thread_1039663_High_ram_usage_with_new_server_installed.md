---
title: "High ram usage with new server installed"
date: 2009-01-14
forum: Server Platforms
---

### Post by Farner on 2009-01-14
Hi
I've just installed Ubuntu 8.10 Server x86 on my newly installed server. I'm using it as a fileserver and router. The system I am running it on is:
AMD64 3500+
1GB DDR Ram
1TB HDD

I don't have much experiance with linux, altho I would suspect only connecting to the server with SSH and not running any programs would take alot less then 900MB of ram.

When I'm writing top this is how it looks like: ```
top - 01:12:56 up 11 min,  2 users,  load average: 0.00, 0.03, 0.03
Mem:   1033400k total,   934644k used,    98756k free,    11312k buffers
Swap:   498004k total,        0k used,   498004k free,   862928k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4446 mysql     20   0  124m  16m 4852 S  0.3  1.6   0:00.28 mysqld
    1 root      20   0  3056 1888  564 S  0.0  0.2   0:01.25 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
  156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue
  160 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
  200 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  201 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  202 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  244 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1262 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd
 1263 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1288 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1289 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux
 1291 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 2041 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 2045 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 2046 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 2047 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
 2048 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3
 2083 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 scsi_eh_4
 2084 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 scsi_eh_5
 2112 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_6
 2113 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_7
 2122 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_8
 2123 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_9
 2251 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 kjournald

```

---

### Post by spiderbatdad on 2009-01-14
[http://www.novell.com/coolsolutions/feature/18990.html](http://www.novell.com/coolsolutions/feature/18990.html)

The above article exlpains how linux uses free ram to cache the system disk for performance. Your memory is not all used up. As applications require ram, the ram is freed up for the applications. There is also a brief discission on how to set swappiness lower in /etc/sysctl.conf to make the system less likely to use swap...not necessarily good in server applications, but perhaps for desktops.

---

### Post by blackened on 2009-01-14
I would recommend using the free command to check total memory usage. Top is better for scrutinizing individual processes (though htop is even better for advanced sorting methods).

```
free -m
```

---

### Post by Farner on 2009-01-14
Thanks for the quick answer :)

Seems like I don't have to worry then :) cheerios

---

