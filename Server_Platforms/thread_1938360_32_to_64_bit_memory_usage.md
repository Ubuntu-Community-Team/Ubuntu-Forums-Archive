---
title: "32 to 64 bit memory usage"
date: 2012-03-09
forum: Server Platforms
---

### Post by berinde on 2012-03-09
Searched for similar post. Apologies if already posted.

Hello All,

I run a little home server for the purpose of file sharing and code compiling (Computer Science student). The distribution I chose was Ubuntu Server 10.04. The first machine that I was using was an old Dell Dimension 4300 that was given to me. I have found that it was a good learning environment, but needed something a bit (or 32) more powerful. I now have a Lenovo ThinkCentre that can handle the tasks much easier. 

After booting the Dell used ~30 MB of memory with the rest cached. The Lenovo now uses ~200 with the rest cached. My question is this: Would moving from 32 to 64 bit actually increase system memory usage by such a large amount?

Specs:
Dell Dimension 4300
Pentium 4 @ 1.4GHz
1024MB DDR1
40GB Hard Drive

Lenovo M58p
Core 2 Duo @ 3.0GHz
4096MB DDR3
160GB Hard Drive

---

### Post by Basher101 on 2012-03-09
i am not entireley sure, **_BUT_** what i have expirienced in using both Ubuntu and Windows 7 on various machines, i noticed how the RAM usage also was different despite having identical setups on all the machines. The biggest memory usage was seen on the devices with the biggest RAM. So my guess is, the OS simply "adjusts" the memory usage to the total RAM available, using much less if only 1 GB is there to leave enough space for other applications and using more with 8 GB since there is space for tons of applications. 

Again, this is only my observation based on expirience.

Hope this helped


regards

---

### Post by CharlesA on 2012-03-09
The memory usage has renamed pretty much the same when I checked a 32-bit install vs a 64-bit install.

I've been running 10.04 server on my new box (i7, 16GB RAM) for a while and it's using more memory than it did on my old box (dual core, 6GB RAM), but the difference isn't much.

---

