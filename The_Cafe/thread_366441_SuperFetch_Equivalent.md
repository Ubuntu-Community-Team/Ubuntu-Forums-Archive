---
title: "SuperFetch Equivalent"
date: 2007-02-20
forum: The Cafe
---

### Post by DivineOmega on 2007-02-20
> SuperFetch caches frequently-used applications and documents in memory, and keeps track of when commonly used applications are usually loaded, so that they can be pre-cached.

Does Ubuntu (or should I say Linux) have an equivalent of this SuperFetch feature now present in Windows Vista?

I noticed most of my RAM is used as 'cache', is this the same idea? If not, what it this 'cache' used for?

Any other details are much appreciated.

---

### Post by saulgoode on 2007-02-20
'Cache' refers to disk data that is kept in RAM just in case it is accessed again. This can greatly speed things up if you are repeatedly fetching the same data from the disk. Technically, it is not really being "used" as it will be overwritten if an application needs the memory.

The problem arises in determining whether to keep a non-running application in memory (reducing the memory available for caching) or to save that application to the swap partition (and thereby gaining memory for the disk cache). To a large extent, this is determined by how you use your computer: if you don't want delays when you switch back and forth between OOo to Mozilla, for example, you will want to have very little caching and retain both programs in memory. If you are editing images in the GIMP (or using a video editor) or compiling large projects, caching becomes very important and non-running programs should be swapped out of memory.

The Linux kernel provides a way for you to fine tune the amount of swapping that take place by changing the contents of "/proc/sys/vm/swappiness". This file holds a number between 0 and 100; where "0" means keep applications in memory as much as possible and "100" means to swap out programs that aren't running. You can set this value anywhere between the two extremes, providing a proportional prioritization to suit your preferences. 

My guess is that SuperFetch is Microsoft's way of addressing the same problem.

---

### Post by gruffy-06 on 2007-12-26
Just install the *preload* package from the Universe repository.

---

