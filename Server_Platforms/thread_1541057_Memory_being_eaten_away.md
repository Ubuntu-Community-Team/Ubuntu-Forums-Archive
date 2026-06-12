---
title: "Memory being eaten away"
date: 2010-07-28
forum: Server Platforms
---

### Post by dmaxel on 2010-07-28
Something seems to be eating up my memory big time, and at a pretty fast rate. The server has a Quad Core and 2GB running very low traffic sites. Here's the output of some commands:
```
gamerboss@dserver:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1974       1958         15          0          2         38
-/+ buffers/cache:       1917         56
Swap:         2831        166       2665
```Swap may not be used as much at this current time, but it's growing rapidly.
```
gamerboss@dserver:~$ ps -aux
<SNIP OF PROCESSES THAT USE VIRTUALLY NO MEMORY>
root      1793  0.0  0.1  35340  3596 ?        S    Jul27   0:01 ddclient - sleeping for 530 seconds
postfix   1977  0.0  0.0  41780   752 ?        S    Jul27   0:00 tlsmgr -l -t unix -u -c
root      2381  0.0  0.2 248992  4864 ?        Ss   Jul27   0:00 /usr/sbin/apache2 -k start
daemon    2383  0.0  0.0 119648  1392 ?        S    Jul27   0:00 /usr/sbin/fcgi-pm -k start
root      4207  0.0  0.0  17140   136 ?        S<   04:01   0:00 udevd --daemon
root      4208  0.0  0.0  17140   136 ?        S<   04:01   0:00 udevd --daemon
daemon    4291  0.0  4.0 408456 82352 ?        S    04:18   0:07 /usr/sbin/apache2 -k start
**daemon    5786  0.3 34.0 968724 688108 ?       S    12:37   0:33 /usr/sbin/apache2 -k start**
daemon    6030  0.0  5.0 337876 103012 ?       S    13:48   0:05 /usr/sbin/apache2 -k start
[B]daemon    6045  0.3 19.5 629748 396196 ?       S    13:53   0:18 /usr/sbin/apache2 -k start
daemon    6046  0.2 18.6 619924 376464 ?       S    13:53   0:17 /usr/sbin/apache2 -k start[/B]
postfix   6072  0.0  0.0  39260   996 ?        S    14:05   0:00 pickup -l -t fifo -u -c
daemon    6230  0.0  2.2 281644 46180 ?        S    14:57   0:01 /usr/sbin/apache2 -k start
daemon    6231  0.1  1.9 276504 40052 ?        S    14:57   0:02 /usr/sbin/apache2 -k start
daemon    6264  0.0  1.6 275836 32412 ?        S    15:00   0:00 /usr/sbin/apache2 -k start
daemon    6265  0.0  1.5 268868 30532 ?        S    15:00   0:00 /usr/sbin/apache2 -k start
**daemon    6268  0.3  7.3 385912 149144 ?       S    15:00   0:06 /usr/sbin/apache2 -k start**
root      6708  0.0  0.1  70608  3180 ?        Ss   15:24   0:00 sshd: gamerboss [priv]
1000      6774  0.0  0.0  70608  1616 ?        S    15:24   0:00 sshd: gamerboss@pts/0
1000      6775  0.0  0.1  20692  3428 pts/0    Ss   15:24   0:00 -bash
1000      6812  0.0  0.0  15252  1216 pts/0    R+   15:33   0:00 ps -aux
```As we can see, apache (in bold) is using up a lot of memory. But I'm not sure why...any help? And since I don't see PHP in there anywhere, so I'm assuming that it's part of the apache processes, right?

---

