---
title: "High CPU load averages"
date: 2017-03-30
forum: Server Platforms
---

### Post by Wayne_D_Russell on 2017-03-30
Hi,

I have a server with high average load when it's not doing much work see below:

I added an additional processor yesterday but it has not made any difference to the load averages.

I am using fail2ban and wonder if that would cause this problem?

free -h shows:
```
total used free shared buffers cached
Mem: 1.1G 964M 150M 14M 147M 477M
-/+ buffers/cache: 339M 776M
Swap: 2.0G 6.3M 2.0G
```

Using "ps awwlx --sort=vsz". This shows processes sorted by virtual sizes I have included the bigest ones below:

```
F UID PID PPID PRI NI VSZ RSS WCHAN STAT TTY TIME COMMAND
1 1000 1178 1 20 0 639220 53452 futex_ Sl ? 2:25 ./insync-headless start
4 104 1058 1 20 0 878608 77380 poll_s Ssl ? 1:11 /usr/sbin/mysqld
5 0 1354 1 20 0 1167388 14868 poll_s Sl ? 1:01 /usr/bin/python /usr/bin/fail2ban-server -b -s /var/run/fail2ban/fail2ban.sock -p /var/run/fail2ban/fail2ban.pid
```


```
Operating system Ubuntu Linux 14.04.1
Kernel and CPU Linux 3.13.0-76-generic on x86_64
Processor information Intel(R) Xeon(R) CPU E5-2650 v2 @ 2.60GHz, 2 cores
Running processes 244
CPU load averages 2.00 (1 min) 2.02 (5 mins) 2.05 (15 mins)
CPU usage 0% user, 0% kernel, 0% IO, 100% idle
Real memory 385.79 MB used, 1.09 GB total
Virtual memory 12.76 MB used, 2 GB total
Local disk space 8.41 GB used, 49.08 GB total
```

Regards

Wayne

---

### Post by howefield on 2017-03-30
Thread moved to the "*Server Platforms*" forum for a better fit and code tags added.

---

### Post by Doug S on 2017-04-01
Might you have two processes stuck in uninterruptible sleep? Check via:```
ps -e -o state,pid,cmd | grep ^D
```

EDIT: I forgot to mention: Your kernel is really old. There was a time when reported load averages could be wrong, under certain conditions.

---

