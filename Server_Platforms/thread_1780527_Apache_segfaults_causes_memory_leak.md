---
title: "Apache segfaults causes memory leak"
date: 2011-06-12
forum: Server Platforms
---

### Post by xoxbet on 2011-06-12
HI,

I'm having some strange issues with apache. Time by time it segfaults, eats all available memory (including swap) and makes server non responding.

Ubuntu Server 10.04.2 LTS

Some strange logs:
Jun 12 12:00:18 *** kernel: [40767.969443] apache2[7635]: segfault at 726f7272 ip 00007f13a31f3f16 sp 00007fff6f740ea0 error 4 in libapr-1.so.0.3.8[7f13a31d7000+35000]
Jun 11 19:54:23 *** kernel: [1673722.930582]  [<ffffffff812bd693>] call_rwsem_down_write_failed+0x13/0x20
Jun 11 19:54:23 *** kernel: [1673722.930570]  [<ffffffff8155b265>] rwsem_down_failed_common+0x95/0x1f0

Apache error.log
apache2: tpp.c:63: __pthread_tpp_change_priority: Assertion `new_prio == -1 || (new_prio >= __sched_fifo_min_prio && new_prio <= __sched_fifo_max_prio)' failed.
7f4bb9afb000-7f4bb9afe000 r-xp 00000000 09:01 9063                       /lib/libgpg-error.so.0.4.0


How to find out which apache module is failing or is it apache itself?

---

### Post by webofunni on 2011-06-12
Unload each module one by one and try. Remove one module and run apache for a period of time and another etc. that will help to find the exact module that caused the issue.

---

### Post by xoxbet on 2011-06-13
I found out, that possibly (hour running without problems) cause of the problem was corrupted myisam tables. On busy website (magento cms) this caused apache (or it'smodules) to make some unusual stuff.

myisamchk was a key :)

---

### Post by webofunni on 2011-06-13
I guess PHP module will be handling the mysql database. Is there a module in apache that connects to mysql directly ?

---

