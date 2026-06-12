---
title: "Virtual Memory/Swap Question"
date: 2010-07-16
forum: Server Platforms
---

### Post by tyraen on 2010-07-16
This might be an obvious question. I'm looking at a server (not mine) running Apache 2, MySQL, and a couple of Java apps. It has 4 processors, 12GB of RAM... but only 2GB of swap. That part seems pretty strange to me; it's not my server, but shouldn't it have 1.5-2.0 * the RAM in swap space?

I've been watching the CPU usage of Apache spike up really high, where a process will take > 60% of a CPU. I believe it's only handling a single request for this. I've been trying to figure out why the CPU usage is so high on this hefty server, when the CPU usage is much more reasonable on my dev box.

The other strange thing is that some of the procs, namely the Java apps, together have over 5GB in virtual memory. My operating systems is a little rusty, but where exactly is that being held onto if not in the swap? The memory usage of the machine is reported as roughly 2GB/12GB, and swap is only 50MB/2GB.

Any ideas? Thanks.

---

### Post by ruffEdgz on 2010-07-16
I think that 'rule of thumb' can still apply but it depends on what you are trying to run.

Now with the addition of more RAM in servers (storage is cheap but so can be RAM), there hasn't been a need for swap to be 2x more then your RAM.

Certain DB's or application might recommend or require a certain amount of RAM because they don't want to take the risk of a server not being able to handle large amounts of load at one time but usually you can get away with 2GB or 4GB of RAM. An example of this is Oracle requires you to have about .75 * physical RAM = SWAP size.

It never hurts to have a lot of swap but it might not be needed depending on what you system is actually doing :D

---

### Post by tyraen on 2010-07-16
Alright. Does it seem strange to you that the virtual memory reported isn't being reflected anywhere? I thought that it would show up somewhere, like under the swap or something.

---

### Post by lukeiamyourfather on 2010-07-16
Swap in Linux is only used when the physical memory is completely full (paging in Windows is a completely different story). I usually make the swap partition half the size of the physical memory, or on a system with not a lot of memory the same as the physical memory. If a system needs two times as much swap as it has physical memory to get the job done then it just plain needs more memory. Cheers!

---

### Post by tyraen on 2010-07-16
Alright; but virtual memory is still held somewhere isn't it? I always thought it would show up in the swap. Is there a way to find out what storage medium the system is using for virtual memory? Or how much of the RAM is being consumed by virtual memory? Something just seems odd about the situation.

---

### Post by lukeiamyourfather on 2010-07-19
> **tyraen said:**
> Alright; but virtual memory is still held somewhere isn't it? I always thought it would show up in the swap. Is there a way to find out what storage medium the system is using for virtual memory? Or how much of the RAM is being consumed by virtual memory? Something just seems odd about the situation.

I'm not really following what you're asking for. Virtual memory means the addressable memory space of both the physical memory plus the swap, and the programs don't know the difference since the kernel manages everything. Again, the swap is only used when the physical memory is fully utilized.

Are you saying the term "virtual memory" instead of a Java virtual machine stack size (e.g. memory limit)? In that case only memory that is actually in use will show up in the resource monitors, not the maximum limit. The maximum memory limit isn't "held" anywhere.

---

### Post by tyraen on 2010-07-19
I think I am just confusing myself. htop says 2.5GB used overall, and that an app has reporting 4.5GB of virtual memory. So that virtual memory number is just the memory space it potentially can address? I see.

I think that more or less clears it up. I was thinking that the virtual memory figure was all the memory the app had allocated, including in-use memory that had gone to swap--but then the swap wasn't reporting any usage, which confused me.

---

### Post by beth262 on 2010-10-22
Likewise, I'm also being confused with the terms relating to virtual memory. The concept is more of an abstract than a spatial reality.

---

### Post by BkkBonanza on 2010-10-23
The virtual memory reported by tools like htop is actually a figure that indicates memory requested by an app whether it is actually used or not. It seems some processes request a large chunk of memory and then don't use it. I believe linux doesn't map the pages into RAM (lock them down) until they are actually used and so often you'll see the res and shr columns being much less. I haven't found a detailed explanation of this but I believe it's roughly correct.

The only reason to have a swap size bigger than RAM is if you need to hibernate into that space. Most servers don't hibernate and reserving that much space for swap would be a waste of disk space. Even 2GB is pretty much a waste. With 12 GB of RAM it's highly unlikely that swap is actually going to be needed. The kernel may use a bit since it's there, and it sometimes moves pages off to swap when it sees them as lower priority than cache, but when it uses swap at the same time that a lot of RAM is available it's not critical demand. At least this is my understanding after years of using Linux. Definitive detailed explanations seem pretty hard to find.

---

