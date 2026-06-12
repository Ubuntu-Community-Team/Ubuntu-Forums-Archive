---
title: "Can Not Allocate Memory"
date: 2011-05-02
forum: Server Platforms
---

### Post by cakka on 2011-05-02
Hello,

i am learning about ubuntu
today i try to check the ram usage in my server with : free -m
but, i get message : allocate memory...

why this problem can happened ?

thanks

---

### Post by volkswagner on 2011-05-02
What do you get for the following command?

```
cat /proc/meminfo
```

---

### Post by cakka on 2011-05-05
> **volkswagner said:**
> What do you get for the following command?

```
cat /proc/meminfo
```


i got this on my console 

> 
root@server1:/home/XXXXXXXXXXXXXXX# cat /proc/meminfo
MemTotal:       524288 kB
MemFree:         81896 kB
Buffers:             0 kB
Cached:              0 kB
SwapCached:          0 kB
Active:              0 kB
Inactive:            0 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       524288 kB
LowFree:         81896 kB
SwapTotal:           0 kB
SwapFree:            0 kB
Dirty:             104 kB
Writeback:           0 kB
AnonPages:           0 kB
Mapped:              0 kB
Slab:                0 kB
PageTables:          0 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:         0 kB
Committed_AS:        0 kB
VmallocTotal:        0 kB
VmallocUsed:         0 kB
VmallocChunk:        0 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
Hugepagesize:     2048 kB
root@server1:/home/XXXXXXXXXXXXXXX#

it is not normal, apache use memory on my server more than 300MB
my site is just a regular blog with 2 company profile
which just use low resource

what do you think about this ?

thanks

---

