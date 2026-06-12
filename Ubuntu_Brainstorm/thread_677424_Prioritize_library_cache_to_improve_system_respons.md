---
title: "Prioritize library cache to improve system responsiveness"
date: 2008-01-24
forum: Ubuntu Brainstorm
---

### Post by Milk &amp; Toast &amp; Honey on 2008-01-24
Hi, this idea is based on [my (unsolved) thread]("http://ubuntuforums.org/showthread.php?t=630157"), please read the first post on that thread to get a better understanding on my idea.

Everytime I copied files that has bigger size than my physical memory, I have a "slow" / non-responsive system afterwards, e.g. opening a previously closed programs taking a long time, which is won't happened if I copied files that have smaller size than my physical memory.

My assumption: this is because the program's dependent files (the binary, library, etc) cache got flushed by the file's cache. "Get flushed" here doesn't means get swapped.

My idea is, can the developers made the system to prefer the program's cache (binary, library and/or other dependant files) to stay in the memory and won't get replaced by the other file cache?
I think if the files that resides in /bin, /lib, /usr can have a higher priority to stay cached on the memory, the system will stay responsive, even after / while copying gigabytes of files (that notabene, resides in directories other than /bin, /lib or /usr) .

Of course, the program's cache it self have priority against them self, if the system need more memory to cache other program's binary / library, then the older program's cache, get replaced by the new demand, but will not get replaced by non-library files.
This is like a tunable parameter, something like percentage (of system memory) to reserved for the library cache, and to prevent from eating all physical memory to cache the library.
However, this will not make the system become responsive the first time it's booted, because (obviously) no user program's library cached yet, but this can add responsiveness in the long run.

Please note, this idea is based on my (non-developer, non-technical) assumption, so I might be wrong, please bear with me :) .

Comments anyone?

---

### Post by lexen on 2008-01-25
I didn't read your original post, but I get what your saying.  It sounds like a good idea.  I must disagree with you about one thing though, I don't think it should be based on percentage.  Here is how I think it should work with 1GB of ram:

300MB - Programs / OS
724 - Available for Coping / other Programs

The ram shouldn't drop programs you are currently using, it should only use the remaining space, possibly leaving a little open on the ram so you don't have slow down.  If you have almost all of your ram filled up, then you shouldn't be surprised when the copy take a while.


Those are my two cents,
Lexen

---

### Post by [h2o] on 2008-01-27
I am not sure how the kernel does it, but I don't think data when copying files should really end up in memory at all. That's why we have DMA-transfers. Are you sure your disks are setup properly for DMA?

---

### Post by Quikee on 2008-01-27
> **'[h2o] said:**
> I am not sure how the kernel does it, but I don't think data when copying files should really end up in memory at all. That's why we have DMA-transfers. Are you sure your disks are setup properly for DMA?

Hm.. DMA just means copying to (main) memory without going through CPU (Direct Memory Access). ;) So even if you copy from one device to another (like hdd to hdd) it always goes through main memory (with or without CPU supervision).

---

### Post by Milk &amp; Toast &amp; Honey on 2008-02-12
Hi all, I'm sorry I just reply this thread  now, I "lost in space" for couple weeks or so -- had a problem with my ISP.

> **lexen said:**
> I didn't read your original post, but I get what your saying.  It sounds like a good idea.  I must disagree with you about one thing though, I don't think it should be based on percentage.  Here is how I think it should work with 1GB of ram:

300MB - Programs / OS
724 - Available for Coping / other Programs

The ram shouldn't drop programs you are currently using, it should only use the remaining space, possibly leaving a little open on the ram so you don't have slow down.  If you have almost all of your ram filled up, then you shouldn't be surprised when the copy take a while.


Lexen,
I think the kernel do only use the remaining space for file copying (it depends on how you set your vm.swappiness value, though). 
But the problem is, it'll replace the library cache (if the file size is way too big), providing a space for file's content cache, whereas I think it's better to not drop the library cache (which resides in /usr, /lib, etc...). 
So, program's in memory and library cache are two different things.

About your input, wouldn't be better if we specified based on percentage? 
Considering everyone's PC had a various range of memory, so I think percentage would have a more universal value to various machine.

> I am not sure how the kernel does it, but I don't think data when copying files should really end up in memory at all. That's why we have DMA-transfers. Are you sure your disks are setup properly for DMA?
Data do cached to memory due file copying, I think it basically is the same  thing as reading the file contents.
I've tried to copy a cold data, the second time I copy that data, it took (a lot) less time to complete.

---

### Post by [h2o] on 2008-02-14
> **Quikee said:**
> Hm.. DMA just means copying to (main) memory without going through CPU (Direct Memory Access). ;) So even if you copy from one device to another (like hdd to hdd) it always goes through main memory (with or without CPU supervision).

No. I am pretty sure DMA handles hdd to hdd copying without using the CPU.

---

### Post by Quikee on 2008-02-16
> **'[h2o] said:**
> No. I am pretty sure DMA handles hdd to hdd copying without using the CPU.

And what did I say? In DMA, CPU doesn't do any 'copying' job but a I/O controller does it instead.. however an I/O controller can still only copy to memory, and can not interact directly with another I/O controller, which is then related to what you said:

> **'[h2o] said:**
> I am not sure how the kernel does it, but I don't think data when copying files should really end up in memory at all. That's why we have DMA-transfers. Are you sure your disks are setup properly for DMA?

This is a wrong assumption, because even if DMA is used copied files end up in main memory anyway regardless if the copying was done programmatic (using CPU) or it was done by an I/O controller using DMA.

---

