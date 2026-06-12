---
title: "VM Hard Drive Benchmarks"
date: 2013-07-20
forum: Virtualisation
---

### Post by petsoukos on 2013-07-20
Hey,

I run a Crystal Disk Mark test on a Windows 7 (64bit) VM, but I don't know if the results are any good.

The drive is a 5-year old secondary storage. 250GB Western Digital (AAKS) HDD

Here are the results:
[IMG]http://petsoukos.com/Win7VM-DiskTest.png[/IMG]

---

### Post by 2F4U on 2013-07-20
I am not sure what you attempt to measure. Since you are measuring from within a VM, you measure virtualized hardware. If it is slow, it may be due to the host system doing other work. If it is fast, it may be even faster if directly run on the host. If you do the benchmarking within the VM, part of the result will be the overhead imposed by the virtualization technology and the host system.

---

