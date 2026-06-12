---
title: "What is the Linux kernel? What was Thorvalds' main contribution?"
date: 2011-10-29
forum: The Cafe
---

### Post by yc2 on 2011-10-29
Hi,

**1. What is the Linux kernel?**
What is the Linux kernel? When I try to read about it I get the impression that the kernel mainly consists of the device drivers? Is it that simple?

**2. What was Thorvalds' main contribution?**
"*In 1991 Thorvalds wrote the first Linux kernel. This made it possible to use the programs collected under the GNU project (Stallman was a main guy there)*" I think this is how the first Linux kernel often is described. But what was the major contribution of the kernel at that time? Didn't they have device drivers for the disks then? (I don't even remember if the disks usually were hard or floppy at that time, even though I wrote my first program in '74 ;) )  Were there maybe only drivers for the disks in DOS and Torvalds major contribution was to write the first free disk-driver routines???? (I guess drivers for the screen/graphics card were also needed?) (I'm just guessing here) I think Thorvalds had access to an assembler ("assembly language compiler").

**3. How do the programs interface with the Linux kernel?**
I completely lack knowledge about this. Lets say we run the command "cp file-a file-b" on the hard disk. Who is doing what? I guess at least the following programs are of major importance:
1. cp command
2. kernel
3. file system
4. disk controller software
(If fragmentation has occurred, I guess the filesystem is the one splitting up a large file to fit into the holes available?)

Sorry if my question is not clear, I find it hard to grasp this subject.

Thanks a lot. I am on a trip and can not reply immediately, but I  will definitely try to get a better understanding of this. I will read all contributions carefully :)
Thanks to all guys spending time to reply in ubuntuforums

ycc

---

### Post by elliotn on 2011-10-29
the kernel is the base of the OS, Even Windows have its own

---

### Post by tartalo on 2011-10-29
It might help:
[http://en.wikipedia.org/wiki/Kernel_%28computing%29](http://en.wikipedia.org/wiki/Kernel_%28computing%29)
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)
[http://en.wikipedia.org/wiki/Tanenbaum%E2%80%93Torvalds_debate](http://en.wikipedia.org/wiki/Tanenbaum%E2%80%93Torvalds_debate)
[http://en.wikipedia.org/wiki/GNU](http://en.wikipedia.org/wiki/GNU)
[http://en.wikipedia.org/wiki/GNU_Hurd](http://en.wikipedia.org/wiki/GNU_Hurd)
[http://en.wikipedia.org/wiki/History_of_Linux](http://en.wikipedia.org/wiki/History_of_Linux)

---

### Post by yc2 on 2011-10-30
Thanks. Good links.

Ppl from sweclockers.com (Swedish) gave me this link, it seems to be on the spot:
[http://tuxradar.com/content/how-linux-kernel-works](http://tuxradar.com/content/how-linux-kernel-works)

I put "solved" on this thread.

---

