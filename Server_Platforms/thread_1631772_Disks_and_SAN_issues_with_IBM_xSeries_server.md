---
title: "Disks and SAN issues with IBM xSeries server"
date: 2010-11-27
forum: Server Platforms
---

### Post by Abu_Dayya on 2010-11-27
I installed Ubuntu 9.04 on an IBM xSeries 346 server, in a dual mode setup with windows 2003nt I guess. I don't usually work with xSeries machines, hence my problems.

- There are two 73GB disks on there, and configured with RAID (don't know which one exactly, but I'm assuming RAID1) which I didn't know of in the begining. To install ubuntu, I partitioned the C: drive in windows and made D:. then when I went ahead and began installing ubuntu, I found 4 disks. Two for windows and two empty ones, which are the ones I partitioned to make the D: drive. So I chose one of the empty ones and installed ubuntu. Now in Ubuntu I see the two Windows disks, plus an empty D: disk???

Is there a way to clean this mess up? either by running ubuntu in RAID1 on the two emtpy disks or something?

- The second (and most important) issue, is that I have a 1TB disk on a SAN connected to the server through two Fibre Channel cards. The disk is accessable in Windows, but I don't see it in Ubuntu. when I run lspci I see two fibre channels apearing

```
Fibre Channel: QLogic Corp. QLA2300 64-bit fibre channel Adapter
```
So, what to do to get the disk in Ubuntu?

Thanks

---

### Post by Abu_Dayya on 2010-11-29
Anyone??

---

