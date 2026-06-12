---
title: "Huge Page Support"
date: 2008-07-24
forum: Server Platforms
---

### Post by shank15217 on 2008-07-24
Hi all, 

I just started to use Ubuntu server over RHEL5 and so far I have enjoyed it however there are some features that are not present. One such issue is the absense of HugePages. Does Ubuntu 8.04 packaged kernel not support Linux HugePages or is this feature internal and dynamic to the kernel now? RHEL5 uses 2.6.18.

root@mainframe:~# cat /proc/meminfo
MemTotal:      7990024 kB
MemFree:       7585928 kB
Buffers:         22548 kB
Cached:          81756 kB
SwapCached:          0 kB
Active:          64660 kB
Inactive:        65500 kB
SwapTotal:     6385796 kB
SwapFree:      6385796 kB
Dirty:               0 kB
Writeback:           0 kB
AnonPages:       25868 kB
Mapped:           6868 kB
Slab:            22556 kB
SReclaimable:     9108 kB
SUnreclaim:      13448 kB
PageTables:       1504 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:  10380808 kB
Committed_AS:   121248 kB
VmallocTotal: 34359738367 kB
VmallocUsed:      3800 kB
VmallocChunk: 34359734343 kB
**generally HugePages_Total: 0 <- this line is not there
**generally HugePages_Free: 0 <- this line is not there
**generally HugePagesise: 2048kB <- this line is not there

root@mainframe:~# uname -a
Linux mainframe 2.6.24-19-xen #1 SMP Sat Jul 12 00:15:59 UTC 2008 x86_64 GNU/Linux

Some insight would be very appreciated.

Thanks,

Shank

---

### Post by windependence on 2008-07-25
Looks like a kernel recompile to me.

If it's a deal killer for Ubuntu, you could always use CentOS if the licensing cost was an issue for RedHat.

-Tim

---

### Post by shank15217 on 2008-07-28
It is a deal killer for Ubuntu if it wants to penetrate further into enterprise Linux. I have basically verified that yes, Ubuntu by default does not enable this feature. Considering the fact it has a ton of improvements in the latest kernel and a far better repository system, I wish this could be investigated further.

---

