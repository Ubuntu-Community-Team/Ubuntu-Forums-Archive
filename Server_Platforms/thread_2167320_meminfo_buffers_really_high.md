---
title: "meminfo buffers really high"
date: 2013-08-13
forum: Server Platforms
---

### Post by smremde on 2013-08-13
Is this normal - I've never seen buffers so high?

$ cat /proc/meminfo 
MemTotal:       16332808 kB
MemFree:         1112264 kB
Buffers:        10630124 kB
Cached:           699400 kB
SwapCached:            0 kB
Active:          3262924 kB
Inactive:        8132004 kB
Active(anon):      27464 kB
Inactive(anon):    38888 kB
Active(file):    3235460 kB
Inactive(file):  8093116 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:        525308 kB
SwapFree:         525308 kB
Dirty:                40 kB
Writeback:             0 kB
AnonPages:         65412 kB
Mapped:            11300 kB
Shmem:               940 kB
Slab:            3674368 kB
SReclaimable:    3652612 kB
SUnreclaim:        21756 kB
KernelStack:        1496 kB
PageTables:         3340 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     8691712 kB
Committed_AS:     594304 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      102232 kB
VmallocChunk:   34359634044 kB
HardwareCorrupted:     0 kB
DirectMap4k:        2048 kB
DirectMap2M:    16691200 kB

---

### Post by davetv on 2013-08-13
Completely normal. Linux is caching programs/files you have closed in case you open them again. There is nothing in swap which is always a good sign.

---

### Post by kpothi on 2013-08-13
It is normal. You may also use `free` command to get an overview of used and free memory in your server.

---

