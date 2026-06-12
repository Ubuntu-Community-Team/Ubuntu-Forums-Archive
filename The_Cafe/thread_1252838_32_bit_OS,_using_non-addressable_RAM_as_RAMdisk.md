---
title: "32 bit OS, using non-addressable RAM as RAMdisk?"
date: 2009-08-29
forum: The Cafe
---

### Post by billdotson on 2009-08-29
Is it possible to have say, 8gb of RAM installed and be able to use the ~4.5-5 gb of unusable RAM as a RAMdisk or does the operating system have to be able to address it to use it, even as a RAMdisk?

I suppose if the OS had to access it you could enable PAE couldn't you? In PAE the applications still can't use more than the 32 bit limitation unless they are coded for PAE but the system could at least use it as a RAMdisk for temporary files (opening encrypted documents, photoshop, swap partition, Windows paging file or anything else that would benefit from using a RAMdisk).

I know how to set one up but don't know if I should go ahead and order more RAM. I have another 1GB on the way anyway but if I had more I could use it as a RAMdisk in my 32 bit operating systems and use it normally in my 64 bit operating systems.

Also, what are some other good uses for a RAMdisk?

---

### Post by MaxIBoy on 2009-08-29
You can compile a "bigmem" kernel, a 32-bit kernel capable of addressing 64 gigs of memory. Each individual program can still only use 4 gigs at a time, though.

If you can't address some memory, it's not addressable and that's it. Non-addressable memory is literally impossible to touch, ramdisk or not.

A good use for a ramdisk is to mirror commonly-accessed but rarely-modified files in memory. This can really speed up your system (as in, Firefox starting in under a second.) 

Putting your swap in a ramdisk is a bad idea. The whole point of swap is to allow more memory than your physical memory, and more memory than your address space. Putting your swap in physical RAM defeats the point of swap.

---

### Post by Frak on 2009-08-29
MaxIBoy beat me to the punch. If you can't see it, tough. You won't ever be able to see it.

EDIT
I think you're getting PAE confused. PAE is a processor extension that allows the processor to allocate RAM according to a 36-bit processor, but run programs as if it were a 32-bit processor. Each app can only address 32-bits, but you can access an overall amount of 36-bits.

---

### Post by chriswyatt on 2009-08-29
I remember RAMdisk in DOS, I thought it was pretty cool, I was easily excited by these things then.

---

### Post by billdotson on 2009-08-29
So I would have to get 64 bit Ubuntu (or some other Linux distribution) or hack XP Pro to allow PAE. As far as I know you can only use PAE on Windows if you have a server version. Blast you Microsoft, there goes my big RAMdisk.

PAE allows up to 64GB up RAM to be used (as in having lots of threads or programs going) but a 32 bit application can't actually use more than 3GB itself unless it is coded to understand that. Is threads the correct term? Is this right?

So what do you mean by commonly accessed files in the memory? Like firefox's cache or copying openoffice 3 run files and accompanying big spreadsheet or word processor files into the ramdisk (since openoffice 3 is probably the absolute slowest program on my Ubuntu install). Any other uses? I was thinking if I could get PAE working in XP and I maxed my RAM capacity out I could have 5gb ramdisk and install some older games into it when I am going to play them (Day of Defeat: Source no more loading times ever!).

My father could probably make good use out of a RAM disk. He has office 2007 and 4GB of ram. He could probably use 1GB of it for the office cache (or copy the office files into it, I don't know) and then run his excel files from it. I showed him openoffice the other day and he liked the free-ness and open source-ness but he said "I need more than 64000 rows. I use way more than that on a regular basis". So you can imagine how big his excel files are.

---

### Post by cariboo on 2009-08-29
You don't have to go with a 64-bit version. The server kernel can access 64Gb ram. All you have to do is install it from the repositories, and you should then be able to use all your ram.

---

### Post by MaxIBoy on 2009-08-30
> **billdotson said:**
> So I would have to get 64 bit Ubuntu (or some other Linux distribution) or hack XP Pro to allow PAE. As far as I know you can only use PAE on Windows if you have a server version. Blast you Microsoft, there goes my big RAMdisk.

PAE allows up to 64GB up RAM to be used (as in having lots of threads or programs going) but a 32 bit application can't actually use more than 3GB itself unless it is coded to understand that. Is threads the correct term? Is this right?

So what do you mean by commonly accessed files in the memory? Like firefox's cache or copying openoffice 3 run files and accompanying big spreadsheet or word processor files into the ramdisk (since openoffice 3 is probably the absolute slowest program on my Ubuntu install). Any other uses? I was thinking if I could get PAE working in XP and I maxed my RAM capacity out I could have 5gb ramdisk and install some older games into it when I am going to play them (Day of Defeat: Source no more loading times ever!).

My father could probably make good use out of a RAM disk. He has office 2007 and 4GB of ram. He could probably use 1GB of it for the office cache (or copy the office files into it, I don't know) and then run his excel files from it. I showed him openoffice the other day and he liked the free-ness and open source-ness but he said "I need more than 64000 rows. I use way more than that on a regular basis". So you can imagine how big his excel files are.


I wrote about speeding up your system with ramdisks in this post:
[http://ubuntuforums.org/showthread.php?t=1217677](http://ubuntuforums.org/showthread.php?t=1217677)


You do not need a 64-bit kernel. You can install the server kernel, but that's really no good for an interactive desktop system. Server kernels are optimized for high throughput but low latency. For a server that's great, but on a desktop the system will feel sluggish (there will be slight delays everywhere and sound will be awful.) 

One option is to compile a 32-bit "bigmem" kernel. Compiling a kernel is detailed in this page:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
Compiling a kernel is something of an involved process. You need to know A LOT of the details about your hardware, and going through all the options can be tedious. However, you get rewarded with a faster, lighter system, more capable of using the unique advantages of your particular hardware. 


Finally, you may find a precompiled "bigmem" kernel that you can use. I know on Debian you can do "sudo apt-get install linux-image-686-bigmem" but that doesn't work on Ubuntu.

---

