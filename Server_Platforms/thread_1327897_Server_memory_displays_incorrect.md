---
title: "Server memory displays incorrect?"
date: 2009-11-15
forum: Server Platforms
---

### Post by R.Bucky on 2009-11-15
I used the **free -m** command to take a look at my memory, only to find out that my system displays 34M free. 
```

free -m
             total       used       free     shared    buffers     cached
Mem:          4054       4020         34          0        225       3401
-/+ buffers/cache:        393       3661
Swap:         3812          0       3811
```


However, htop and other programs shows 3.5GB free. I have 4GB RAM on a 32 bit ubuntu server 8.04 install. Any thoughts on the 34 free? Or, am I just reading the output incorrectly?

---

### Post by Vegan on 2009-11-15
I would not worry about it.

---

### Post by aaronchall on 2009-11-15
> **R.Bucky said:**
> I used the **free -m** command to take a look at my memory, only to find out that my system displays 34M free. 
```

free -m
             total       used       free     shared    buffers     cached
Mem:          4054       4020         34          0        225       3401
-/+ buffers/cache:        393       3661
Swap:         3812          0       3811
```
However, htop and other programs shows 3.5GB free. I have 4GB RAM on a 32 bit ubuntu server 8.04 install. Any thoughts on the 34 free? Or, am I just reading the output incorrectly?

I think it all balances out with the cache... You have 3401 in cached data that can be written to the swap file and free up a lot of system memory.  I just think your computer is doing a good job of managing its resources, but this is more informative than what your other programs are telling you.  Of course, I'm no expert...

---

### Post by unamanic on 2009-11-15
aaronchall is correct, your system is doing a good job managing it's memory.  Cache is room for files that the computer has read from the hard drive and may need to read again.  Since RAM is a lot faster to read than the disk it will speed up the system.  Meanwhile, your applications are using less than 400 MB to store what they need.

Some people freak out about having almost no resources left after cache, but using cache does not hurt resources.  If an application needs the space, the system just drops a file or two from cache to give the room up for the app. And if those files need to be accessed again, they are just read from the disk again.

Bottom line, your system is good, you are not experiencing a memory problem.  Neither is lying to you.  The application that is telling you you have 3.5 GB free is taking into account that it can use all of the space currently allocated for cache if needed.  Free is telling you the same thing with the 3661 number (3661MB/1024 = 3.57GB).

---

### Post by aaronchall on 2009-11-16
Well, thanks Unamaniac, now I feel like a stud.  As I'm now recalling, when your OS uses RAM for Cache, it's temporarily holding stuff that's already on your hard-drive for fast access if needed.  The more it's caching, the quicker your OS or other apps might be.  If another app needs the RAM, it's ok for the cached data to be dropped immediately because it's already on your hard-drive, and can be picked up from the hard drive when needed.

I'm sure (and hope) I'll be corrected if I'm wrong.  But I think what this means is that if you want to know how much system memory (RAM) you have free, from a practical standpoint, it's in the +/- buffers/cache line, but as the cache gets dropped, you may see a bit of a slowdown as the hard drive needs to be accessed more and more...

My thoughts here are, is there a utility to help the system cache more of the hard-drive, because I'm not seeing much being cached on my machine... looks like only about 500Megs is being cached, leaving 1.2 Megs completely free.  Boy I love Ubuntu over XP though (the snail OS)!

---

### Post by R.Bucky on 2009-11-16
That was definitely helpful and informative. I appreciate the thorough explanations, as it helps alleviate my worrying mind!

---

### Post by unamanic on 2009-11-16
aaron, I think caching is dependant on the kernel, I'm not sure how to increase it, but I trust the kernel devs to get it right for most people.

---

