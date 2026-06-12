---
title: "Multi-core performance difference between two machines"
date: 2013-03-15
forum: Server Platforms
---

### Post by kmcclure on 2013-03-15
We have two servers that are very similar configurations, but when running the same custom in-house application, the performance numbers are substantially different.  

Here are the server specs
Server1
Dell R815,  opteron 6168,  1.9 GHz,  64GB DDR3 1333 ram,  48 cores,  Ubuntu 10.10

Server2
Dell R815, opteron 6238, 2.6 GHz, 128GB DDR3 1600 ram, 48 cores  Ubuntu 10.4.4 LTS

Both servers have identical bios settings with node interleaving off, and all power related settings on max performance.  NUMA is turned off on both machines, and both have base installations with only the packages needed for NFS, SSH, monitoring utilities, and our application.  Both have the same version of our in-house application, and it is configured the same on both machines.  Both machines have all cores at or near 100% all of the time.

The strange thing is server2 is only performing about 20% of the work that server1 is!  I have read about a large increase in context switching latency between the 2.6 and 3.2 kernels, but that doesn't apply in this case. 

QUESTION:  How do I troubleshoot this discrepancy in performance between the two systems?

Thanks!

---

### Post by tgalati4 on 2013-03-15
Install *sysstat* and run* iostat* to gather some statistics from both machines.  Try pulling RAM out of server2 so that it is also 64GB.  Some chipsets declock when RAM is full.  What are the differences in the disk connections between the machines?  Try booting a live session of 10.10 on server2 and rerunning your code. Or try running a live version of 10.04 on server1 and run your code.

What are the RAM speed differences as measured by memtest?  What are the speed differences of L1, L2 speeds?

---

