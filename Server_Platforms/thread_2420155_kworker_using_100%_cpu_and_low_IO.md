---
title: "kworker using 100% cpu and low I/O"
date: 2019-05-31
forum: Server Platforms
---

### Post by DPJB on 2019-05-31
Hi All,

I'm having a problem with a backup server. The server used to work fine and now it is struggling with getting decent disk I/O. The server has a 24 disk RAID array on a MegaRAID SAS-3 3108 card.

Before the problems, copying with around 500 Mb/s was normal. Now I'm happy to get 25 Mb/s.

The main symptom is that there is a kworker thread using 100% CPU. This wasn't there before:

```
top - 08:18:09 up 11:17,  2 users,  load average: 15.95, 15.03, 10.78
Tasks: 524 total,   2 running, 268 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.7 us,  4.0 sy,  0.0 ni, 62.4 id, 29.8 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 65622320 total,   371160 free,   981020 used, 64270140 buff/cache
KiB Swap: 15622136 total, 15619320 free,     2816 used. 63970020 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                                                   
  491 root      20   0       0      0      0 R  99.9  0.0 663:13.14 kworker/u65:11                                                                                                                                                            
 6592 root      20   0 2466316  28696   1996 S  29.3  0.0   1:44.73 pigz                                                                                                                                                                      
 6637 root      20   0 2466316  28840   2140 S  26.7  0.0   1:43.46 pigz                                                                                                                                                                      
 6679 root      20   0 2466316  28696   1996 S  26.4  0.0   1:43.26 pigz                                                                                                                                                                      
 7144 root      20   0 2466316  20168   2048 S  16.8  0.0   0:01.69 pigz                                                                                                                                                                      
 6175 root      20   0   51884  45988   2196 D  14.3  0.1  14:16.87 updatedb.mlocate
```


I've double checked the disk array and it seems in good order. I've updated the server from 16.04 to 18.04, but this didn't matter.

Any help / pointers would be highly appreciated!

Cheers,

Dirk

---

### Post by LHammonds on 2019-05-31
Are you 100% certain the drives are all working?  It sounds like a drive failed and is compensating in real-time to recreate the data.

---

