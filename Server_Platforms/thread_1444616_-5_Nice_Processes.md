---
title: "-5 Nice Processes"
date: 2010-04-01
forum: Server Platforms
---

### Post by Chafnan on 2010-04-01
When I open top and look at the running processes, there a bunch that are -5 in the nice and 0 with everything else. 

Any idea how to fix this?

```
    1 root      20   0  4020   884   600 S  0.0  0.0  0:02.14 /sbin/init
    2 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 kthreadd
    3 root      RT  -5     0     0     0 S  0.0  0.0  0:00.02 migration/0
    4 root      15  -5     0     0     0 S  0.0  0.0  0:00.05 ksoftirqd/0
    5 root      RT  -5     0     0     0 S  0.0  0.0  0:00.00 watchdog/0
    6 root      RT  -5     0     0     0 S  0.0  0.0  0:00.02 migration/1
    7 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 ksoftirqd/1
    8 root      RT  -5     0     0     0 S  0.0  0.0  0:00.00 watchdog/1
    9 root      RT  -5     0     0     0 S  0.0  0.0  0:00.01 migration/2
   10 root      15  -5     0     0     0 S  0.0  0.0  0:00.01 ksoftirqd/2
   11 root      RT  -5     0     0     0 S  0.0  0.0  0:00.00 watchdog/2
   12 root      RT  -5     0     0     0 S  0.0  0.0  0:00.01 migration/3
   13 root      15  -5     0     0     0 S  0.0  0.0  0:00.01 ksoftirqd/3
   14 root      RT  -5     0     0     0 S  0.0  0.0  0:00.00 watchdog/3
   15 root      15  -5     0     0     0 S  0.0  0.0  0:00.19 events/0
   16 root      15  -5     0     0     0 S  0.0  0.0  0:00.01 events/1
   17 root      15  -5     0     0     0 S  0.0  0.0  0:00.09 events/2
   18 root      15  -5     0     0     0 S  0.0  0.0  0:00.01 events/3
   19 root      15  -5     0     0     0 S  0.0  0.0  0:00.03 khelper
   51 root      15  -5     0     0     0 S  0.0  0.0  0:00.09 kblockd/0
   52 root      15  -5     0     0     0 S  0.0  0.0  0:00.04 kblockd/1
   53 root      15  -5     0     0     0 S  0.0  0.0  0:00.05 kblockd/2
   54 root      15  -5     0     0     0 S  0.0  0.0  0:00.02 kblockd/3
   57 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 kacpid
   58 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 kacpi_notify
  129 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 kseriod
  185 root      20   0     0     0     0 S  0.0  0.0  0:00.00 ubstatd
  187 root      20   0     0     0     0 S  0.0  0.0  0:00.00 pdflush
  189 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 kswapd0
  258 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 aio/0
  259 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 aio/1
  260 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 aio/2
  261 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 aio/3
 1233 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 ksnapd
 1592 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 ksuspend_usbd
 1594 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 khubd
 1735 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 ata/0
 1739 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 ata/1
 1741 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 ata/2
 1743 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 ata/3
 1745 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 ata_aux
 1790 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 scsi_eh_0
 1793 root      15  -5     0     0     0 S  0.0  0.0  0:00.00 scsi_eh_1

```

---

### Post by richardjh on 2010-04-06
This is how it is supposed to be.

If you want to make changes to the niceness of running processes you can use renice. 
For example

renice -n 5 -p 2 3 4 5

Would change the priority to 5 for processes 2 3 4 and 5.

A nice value of -5 means it is less nice than 0 and will take priority over these processes.

See man renice for more information, and be aware that you may cause problems to the running of the server.

---

### Post by Chafnan on 2010-04-17
Does that mean that it is normal for all of those processes to be running at -5 or is something wrong with the system?

---

### Post by Xipher on 2010-04-17
It's normal, those are actually kernel processes which should have a higher priority then normal processes.

---

### Post by richardjh on 2010-04-19
Yes, this is how it is supposed to be. 

You may break your setup if you raise the nice value of these processes.

---

