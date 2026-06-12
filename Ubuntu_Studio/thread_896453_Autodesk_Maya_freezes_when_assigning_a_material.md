---
title: "Autodesk Maya freezes when assigning a material"
date: 2008-08-21
forum: Ubuntu Studio
---

### Post by TheOm3ga on 2008-08-21
Hi all,

I finally managed to install Autodesk Maya 8.5 on Ubuntu. The program works very well, I'd say even better than in Windows. BUT there's a problem I've just come across: When I try to assign a material to an object (which is a rather basic and common action), the program exits with no saving possibility. I've tried to reproduce the error launching maya from the console, in order to see the output. This is what it says:

```
om3@fijo:~$ maya

mental ray for Maya 9.0 
mental ray: version 3.6.1.6, 17 Jul 2007, revision 21668
====================================
Cause of memory exception
====================================
  14.914 Mb	Free Memory
   0.000 Mb	Free Swap
  18.000 Mb	Size of alloc
  10.000 Mb	Low Memory Threshold
====================================
Memory use when exception was thrown
====================================
====================================
 182.073 Mb	Peak total size(Estimated)
  72.773 Mb	Peak arena size
====================================
  45.300 Mb	Heap
   0.107 Mb	arguments
  32.812 Mb	MEL
   0.001 Mb	POLY_DRAW_CACHE_DATA
  36.279 Mb	Pixel Map
   0.000 Mb	POLY_DRAW_CACHE_STATIC_DATA
   3.336 Mb	Render Cache
   0.312 Mb	Data Blocks
   0.125 Mb	Transforms
====================================
terminate called after throwing an instance of 'TmemoryException'

maya encountered a fatal error

Signal: 6 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/om3.20080821.1210.ma

```

Looks like the file created in /usr/tmp is a backup of the scene.

What can I do? I don't want to get back to windows just to use one program. However, I'll try to check the performance in virtualbox and see if it works there.

Thanks in advance.

---

### Post by aeiah on 2008-08-22
how much ram does your machine have? because its only saying 14mb free on that error log so it seems pretty much like a standard run-out-of-ram error, although when i used to use it i never ran out of ram, it'd just slow down loads when it struggled with complicated stuff. does this not happen on the windows version then?

you'll probably have more luck on a maya forum than here. i doubt many people on here use maya in linux.

you may have luck with a virtual machine, but you'll have to make sure the virtualisation software you're using allows for windows guests to utilise hardware opengl, else it'll be useless.

the leading ones for linux are virtualbox, xen, kvm and vmware.

---

### Post by TheOm3ga on 2008-08-22
Hi aeiah, thanks for your answer.

I have 1GiB DDR, Maya runs really fast and without a glitch on Windows. I tried using it in virtualbox but the performance made it useless.

I've been googling around and looks like there's no known solution to this problem so I'll continue using it on my Windows partition.

---

