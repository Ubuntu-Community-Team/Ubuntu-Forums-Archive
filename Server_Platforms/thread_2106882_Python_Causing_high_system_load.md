---
title: "Python Causing high system load"
date: 2013-01-20
forum: Server Platforms
---

### Post by jpaytoncfd on 2013-01-20
I am running python for SABnzbd, SickBeard, Couchpotato, and Serviio. I have had a system load above 7.0 for awhile. 

I put all the programs in a rest state and that brought the load down to 3.0

The top command shows:
```
top - 11:04:22 up 1 day, 0 min,  1 user,  load average: 3.63, 3.51, 3.37
Tasks: 131 total,   1 running, 130 sleeping,   0 stopped,   0 zombie
%Cpu(s):  7.1 us, 12.9 sy,  0.0 ni,  8.4 id, 70.0 wa,  0.0 hi,  1.6 si,  0.0 st
KiB Mem:   3791596 total,  3672064 used,   119532 free,  1257216 buffers
KiB Swap:  3932156 total,     5364 used,  3926792 free,  1473852 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND
 1305 jpayton   20   0 1229m 106m 3480 S  36.9  2.9 444:25.58 python
 1918 jpayton   20   0 1353m 160m 3328 S   7.0  4.3 491:31.84 sabnzbdplus
 1463 root      20   0     0    0    0 D   5.7  0.0  39:45.06 flush-252:2
   27 root      20   0     0    0    0 D   5.3  0.0  64:45.85 kswapd0
  918 root      20   0     0    0    0 D   2.0  0.0  28:25.39 kjournald
 1287 root      20   0 1883m 124m 5460 S   1.0  3.4  16:04.43 java
 1155 root      20   0  309m  18m 3200 S   0.3  0.5   3:41.64 ajenti-panel
 1191 root      20   0  953m  61m 3068 S   0.3  1.7  11:07.06 python
 1269 jpayton   20   0 1143m  73m 3384 S   0.3  2.0  12:59.57 python
 7403 jpayton   20   0  124m 4600 3184 S   0.3  0.1   0:50.06 smbd
21598 root      20   0     0    0    0 S   0.3  0.0   0:01.83 kworker/0:1
22062 jpayton   20   0 20492 1536 1104 R   0.3  0.0   0:01.80 top
    1 root      20   0 24556 1476  564 S   0.0  0.0   0:00.66 init
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.02 kthreadd
    3 root      20   0     0    0    0 S   0.0  0.0   0:37.82 ksoftirqd/0
    5 root      20   0     0    0    0 S   0.0  0.0   0:00.44 kworker/u:0
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.09 migration/0

```

Where is the python log and what could be causing this? 
Before I only had a load of 1.0 at full download and unpacking. 
Dual Core 1.6GHz, 4gb Ram, LVM Across 3 drives ext3 filesystem.

---

