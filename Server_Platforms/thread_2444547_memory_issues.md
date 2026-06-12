---
title: "memory issues"
date: 2020-06-01
forum: Server Platforms
---

### Post by bardiamgtgc on 2020-06-01
i bought a third ubuntu server for backups and there is nothing running on it  and the memory usage is 1.3/2gb (checked using free -mh) but there is no process running that is using so much memory most memory usage in top was from top itself using 0.2% 
server is running ubuntu 16.04 with 4.4.0-179-generic kernel
heres the output of cat /proc/meminfo
```

root@berbidvps:~# cat /proc/meminfo
MemTotal:        2048096 kB
MemFree:          250936 kB
MemAvailable:     459256 kB
Buffers:           46120 kB
Cached:           290980 kB
SwapCached:            0 kB
Active:           315340 kB
Inactive:          81040 kB
Active(anon):      63344 kB
Inactive(anon):     4520 kB
Active(file):     251996 kB
Inactive(file):    76520 kB
Unevictable:        3652 kB
Mlocked:            3652 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                36 kB
Writeback:             0 kB
AnonPages:         62984 kB
Mapped:            36556 kB
Shmem:              6152 kB
Slab:              38528 kB
SReclaimable:      22920 kB
SUnreclaim:        15608 kB
KernelStack:        2672 kB
PageTables:         3508 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1024048 kB
Committed_AS:     636584 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       55232 kB
DirectMap2M:     2041856 kB

```

---

### Post by LHammonds on 2020-06-01
The server should not be using that much RAM...but then again, why are  you using 16.04...which is no longer supported?  20.04 is the current  release with kernel 5.4.0-33.

LHammonds

---

### Post by bardiamgtgc on 2020-06-01
i can upgrade it to newer versions if i want to but my question is that can there be a bug in the kernel of something
or maybe the hosting that im buying the server from is sharing resources if possible (the hosting is the cheapest hosting in the whole country and i got from them because i didnt wanted to do much with it its just a backup server)

---

### Post by LHammonds on 2020-06-01
If it is super-cheap hosting, you can bet it will be multi-tenancy.  I run my own hardware so I don't have the experience of how others run their setups and how that translates into what you see inside the OS.

I have run Ubuntu servers with just 512 MB of RAM and they worked well (did not have much RAM needs).  The vast majority of my servers have 1 GB of RAM dedicated to them.

LHammonds

---

