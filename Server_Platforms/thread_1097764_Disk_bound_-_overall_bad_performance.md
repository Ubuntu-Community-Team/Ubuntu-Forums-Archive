---
title: "Disk bound - overall bad performance?"
date: 2009-03-16
forum: Server Platforms
---

### Post by schettj on 2009-03-16
Might be a general ubuntu/linux question, but it's happening on my 8.04 server install

What I'm seeing is, any sustained disk i/o process that pushes significant data to the drive seems to bog down overall system performance other then the disk operation itself.

uname -a
Linux schettino.us 2.6.24-23-server #1 SMP Mon Jan 26 00:55:21 UTC 2009 i686 GNU/Linux

This is on a core 2 duo, 2.4ghz, 6gb ram (2-3gb "free" so no swapping) and 
Drive is MAXTOR STM31000340AS (sata/300)

Formatted as 
/dev/sdc1 on / type ext3 (rw,noatime,errors=remount-ro)

So for example, if I copy 30GB of data onto or off of the drive via gigabit ethernet, or USB attached disk, the copy moves along at disk speed, the cpu load is nice and low, but any interactive or even server based response times are very slow.

Any suggestions as to tuning I might to do up the responsiveness is appreciated.

---

