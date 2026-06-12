---
title: "Ubuntu 14.04.3 server is running very slow?"
date: 2016-02-26
forum: Server Platforms
---

### Post by aristatechnologies2 on 2016-02-26
After Installing Ubuntu 14.04.3 server is running very slow.

Xrog process use 85 % cpu.

Every Application takes more time to open.

_Server Details_
 
hpe Prolaint DL60 Gen9 Server , RAM-64 GB, HDD - 2 TB.

---

### Post by Bucky Ball on 2016-02-26
*Thread moved to **Server Platforms**.*

Perhaps one of your logs is filling up? Check in /var/logs and check the properties of the log files in there. Are there any showing in the multiple Gbs?

---

### Post by MAFoElffen on 2016-02-26
That is just strange.

Did you just say "xorg" is at 85%? Server does no have that... Could you please post the results of:
```

while true; do (echo "%CPU %MEM ARGS $(date)" && ps -e -o pcpu,pmem,args --sort=pcpu | cut -d" " -f1-5 | tail) >> ~/ps.log; sleep 10; done
```
Every 10 seconds, it will log your top 10 processes on your system into a file named ps.log (located in your home directory). Let it run a few minutes ... then kill it by a <Cntrl><C>

---

