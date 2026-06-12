---
title: "more roles for Linux"
date: 2014-04-15
forum: Server Platforms
---

### Post by Vegan on 2014-04-15
so far I have focused more with the Ubuntu distribution and the packages available with tasksel

I have seen lots of mixed shops like mine use it more with Hyper-V now finally fully supporting the kernel properly with a million lines or so of code

so I was looking at a bunch of ideas

SAMBA has been the real role that makes Linux popular as a storage solution. Now along comes Microsoft with their Storage spaces. No more RAID, just a JBOD is now all you need. Anybody use Linux servers that way?

Another idea is for certificates etc following the OpenSSL scandal.

---

### Post by nerdtron on 2014-04-15
Samba is still what we use for storing data over the network if the clients are both windows and linux. Under the filesystems is hardware RAID5 and another system using JBOD with software RAIDZ1
Another one we use is NFS serving only linux clients and it uses JBOD with RAIDZ2.

---

### Post by koenn on 2014-04-16
> **Vegan said:**
> 
SAMBA has been the real role that makes Linux popular as a storage solution. Now along comes Microsoft with their Storage spaces. No more RAID, just a JBOD is now all you need. Anybody use Linux servers that way?


I think you are very confused.
Samba is not about storage, it's about files, and accessing them over a network. That's got nothing to do with storage in terms of block devices, disks, raid, ...

MS storage spaces are apparently more about storage  : it's a way of handling disks and presenting them to the operating system. On first sight, it looks like LVM (appeared in linux in 1998) or even like a respin of MS own dynamic disks or dynamic volumes. 

"Storage Spaces" is  also sort of a software RAID implementation,  with mirror or parity   (again, nothing new there).


So it's not quite clear what your question actually means.

---

### Post by lukeiamyourfather on 2014-04-17
> **Vegan said:**
> Now along comes Microsoft with their Storage spaces. No more RAID, just a JBOD is now all you need. Anybody use Linux servers that way?

Yes, I use Linux that way, as do many other users and organizations. In particular I'm using ZFS on Linux which I mentioned in a reply to another one of your threads.

---

### Post by Vegan on 2014-05-07
I noticed that Supermicro 16 disk server chassis are $1500 which not that expensive, along with a RAID card and some motherboard to power it.

10GBASE-T is needed to reduce bottlenecking

racks of these chassis end up not costing a lot of $

corporate disks are more expensive but a box of 20 disks stacks up nice on a pallet

---

### Post by lukeiamyourfather on 2014-05-20
> **Vegan said:**
> I noticed that Supermicro 16 disk server chassis are $1500 which not that expensive, along with a RAID card and some motherboard to power it.

If you look at their storage server products like this one, it comes with the motherboard and a disk controller (non-RAID, just HBA since ZFS doesn't require a hardware RAID controller). They can be had between $1,500 and $2,000, there are also just JBOD enclosures which can allow many more disks to be attached to a single machine to reduce costs further.

[http://www.supermicro.com/products/system/3U/6037/SSG-6037R-E1R16L.cfm](http://www.supermicro.com/products/system/3U/6037/SSG-6037R-E1R16L.cfm)

> **Vegan said:**
> 10GBASE-T is needed to reduce bottlenecking

It depends on the expected workload and the rest of the network. A large disk array can certainly provide more throughput than gigabit Ethernet can handle. I'm currently using the Intel X540T1 and X540T2 adapters with good results.

> **Vegan said:**
> racks of these chassis end up not costing a lot of $

If cost is a significant factor then there are options which provide storage at an even lower cost like the Backblaze "Storage Pod" idea. There are some commercial products with similar density and cost now too like the 72 drive systems.

[http://blog.backblaze.com/2014/03/19/backblaze-storage-pod-4/](http://blog.backblaze.com/2014/03/19/backblaze-storage-pod-4/)
[http://www.supermicro.com/products/system/4U/6047/SSG-6047R-E1R72L.cfm](http://www.supermicro.com/products/system/4U/6047/SSG-6047R-E1R72L.cfm)

> **Vegan said:**
> corporate disks are more expensive but a box of 20 disks stacks up nice on a pallet

In the case of ZFS, you don't need "enterprise" disks since there are no hardware RAID controllers involved (in most cases). Though there are some perks to using SAS disks like the ability to have a redundant controller via multipathing.

---

