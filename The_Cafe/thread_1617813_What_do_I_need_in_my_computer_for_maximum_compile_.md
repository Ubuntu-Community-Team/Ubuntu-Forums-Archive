---
title: "What do I need in my computer for maximum compile speed?"
date: 2010-11-09
forum: The Cafe
---

### Post by Dustin2128 on 2010-11-09
The case arrived yesterday, next up are the PSU and motherboard. Anyway, I was just wondering: what's the deciding factor in the speed of compiling software? Processor, RAM or a combination?

---

### Post by czr114 on 2010-11-09
Disk access.

---

### Post by 3Miro on 2010-11-09
+1. This happens to be the biggest bottleneck. You an set a parameters to make like
```
 make -j3 
```
which will launch 3 threads to compile software (on my 4 core system with Gentoo, I am using -j6). This does push the CPU every now and then, and it helps reduce the disk access bottleneck, but still, there are huge chunks of time where the CPU is practically idle.

---

### Post by czr114 on 2010-11-09
To clarify:

If you're looking to increase your compile speed, buy a SSD for this new machine, or better yet, put two in RAID 1 for extra data security. If you're doing resource-intensive compiles, you'll want the fault tolerance provided by redundant disks, as that complex project likely has a lot of time invested in it. In terms of performance increase per unit cost, the use of solid state hardware will be far more effective than throwing more megahertz or memory at the problem.

You'll want to use the SSD(s) for your boot, root filesystem, and editor/IDE/compiler working directories.

As far as limited capacity, if that should be a problem, move large media or backup files to magnetic storage and mount it under your home directory.

That will eliminate the largest bottleneck.

---

### Post by szymon_g on 2010-11-09
1. multi-core processor: most applications can be compiled parallelly, so 2 cores (even with lower clock) will do it faster than 1 core (and, of course: 4 faster than 2)
2. memory: code is kept in memory, so faster access to it is a priority

hint: put anything that you wanna compile in tmpfs or ramdisk- thanx that you will avoid reading from harddrive.

---

