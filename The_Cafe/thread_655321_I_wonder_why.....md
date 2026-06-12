---
title: "I wonder why...."
date: 2008-01-01
forum: The Cafe
---

### Post by jobsonandrew on 2008-01-01
I was just sitting here copying a whole load of videos over to my external hard drive and i wondered..
why does Linux copy extremely large amounts of data from one place to another so reliably and efficiently, when windows does it so badly... what is windows doing wrong?

what I mean is, when i copy about 4.5gb worth of data from a dvd to somewhere else, Linux begins doing it immediately, copies at a steady pace throughout the action, and estimates the time very accurately.. whereas windows thinks about it for ages (apparently 'calculating time remaining') stutters along slowly and estimates things really inaccurately...

I'm not starting another 'windows sux0r' thread, so please dont just say something like 'because windoze is poo'.. im actually interested in the details of..**why??**

---

### Post by herbster on 2008-01-01
No expert here but I believe it's to do with the filesystem (ext2/3 vs ntfs) ?

---

### Post by saulgoode on 2008-01-01
The Linux kernel has excellent (and steadily improving) IO scheduling. When multiple processes are accessing different portions of a disk, the kernel will examine those requests and sort them so as to minimize the amount of head movement from one region to another (these "jumps" of the read/write heads have a very adverse effect on access times). The kernel is even capable of switching between optimization methodologies dependent upon the situation (I believe there are seven different IO schedulers available).

A more detailed description of this process is presented in [this Linux Journal article](http://www.linuxjournal.com/article/6931).

I do not know to what extent Windows optimizes IO scheduling but it is apparently not handled very well ([if at all]("http://support.microsoft.com/kb/946676/en-us?spid=12624") :) ).

---

### Post by LaRoza on 2008-01-01
Windows Vista is bad a copying files, I hear the update (SP) improves it, but I don't want the spyware.

Interestingly, I reboot into Linux to copy anything to another partition or flash drive or to burn anything if I happen to be using Windows.

---

### Post by jobsonandrew on 2008-01-01
> the kernel will examine those requests and sort them so as to minimize the amount of head movement from one region to another 

wow... this sounds stupid but i had a feeling that my hard drive was quieter in linux than windows.. must be due to the minimised head movement

---

### Post by ~LoKe on 2008-01-01
> **jobsonandrew said:**
> wow... this sounds stupid but i had a feeling that my hard drive was quieter in linux than windows.. must be due to the minimised head movement

Linux is probably not hitting your hard drive as much.

---

### Post by saulgoode on 2008-01-01
> **jobsonandrew said:**
> wow... this sounds stupid but i had a feeling that my hard drive was quieter in linux than windows.. must be due to the minimised head movement

Linux also has very good disk caching, demand paging, and Copy-On-Write. 

"Caching" means that once data is read from your disk, it is kept in memory (if memory is available) in case you need to read the same data again. 

"Demand paging" means that data is not actually read from a file until needed. For example, if your program opens a library of subroutines for use then the subroutines will only be loaded into memory when they are needed -- and only those subroutines which actually get used (not the entire library).

"Copy-On-Write" (COW) means that data which you copy from one part of the disk to another doesn't actually get written until the destination data gets modified; before that time the destination data merely points to the original location. 

All of these techniques tend to minimize not only the number of filesystem accesses, but the time spent waiting for them as well.

---

### Post by Mazza558 on 2008-01-01
Everyone above is correct. To add to the non-technical side of things, there was continuous improvement by several programmers to the linux kernel which kept streamlining file transfer speeds until they're what they are today.

---

### Post by rune0077 on 2008-01-01
> **jobsonandrew said:**
> 
what I mean is, when i copy about 4.5gb worth of data from a dvd to somewhere else, Linux begins doing it immediately, copies at a steady pace throughout the action, and estimates the time very accurately.. whereas windows thinks about it for ages (apparently 'calculating time remaining') stutters along slowly and estimates things really inaccurately...


With Windows, did you mean XP or Vista? Vista was *really* slow at copying large files when I first got it (and I do mean really slow), but this issue has since been dealt with in an update, and it now seems to copy everything very smoothly and elegantly (though I do think, without having measured it, that Linux does it a bit faster).

Copying large files should also be one of the cases where 64bit shines through (or so I've heard), so if your windows is 32bit and your Linux is 64bit, then this would probably make a big difference in speed.

---

### Post by jobsonandrew on 2008-01-01
I was talking about Vista, but XP was never brilliant at it...

I noticed the increased reliablility and efficiency in both 32 and 64 bit versions of Ubuntu

---

