---
title: "grabbing volatile memory"
date: 2009-11-26
forum: Security
---

### Post by el Tedward on 2009-11-26
I was wondering what tools people have heard of that can be used for grabbing volatile memory off of a live linux system. I've read about some of the cold boot attacks, but I'm looking more for something that I could use without having to reboot or physically pull the RAM out of a system. 

The instructor for my forensics class (not that I would ever go to an internet forum for help on an assignment..), said that I could use dd to grab what's stored in my RAM, but I'm still a bit of a linux n00b and I haven't really been able to figure out what sort of syntax I would use to do that.. 

So, if someone could explain to me how to do this with dd, or mention any tools available for volatile memory "recovery" made for linux systems(it's okay if it's not free, as long it's not designed to work with windowz..) it would be extremely helpful.

---

### Post by Sarmacid on 2009-11-26
> sudo dd if=/dev/mem of=/home/sam/mem.bin bs=1024

The device /dev/mem is your system memory. You can actually copy any block or character device to a file with dd. Memory capture on a fast system, with bs=1024 takes about 60 seconds.There are probably better tools for the job, but dd will do.

---

### Post by The Tronyx on 2009-11-26
> **Sarmacid said:**
> There are probably better tools for the job, but dd will do.

That's one of the best ways to do it.  You can then open the dump in a hex editor or use strings on the file.

You might also want to check out memfetch which you can get at [http://freshmeat.net/projects/memfetch/](http://freshmeat.net/projects/memfetch/)

---

### Post by el Tedward on 2009-12-13
Tried the dd command to dump my mem in ubuntu 9.10. I ran it with sudo and as root, but I keep getting this message regardless:

```
tedward@hdx16:~$ sudo dd if=/dev/mem of=/home/tedward/Desktop/memdump.bin bs=1024
[sudo] password for tedward: 
dd: reading `/dev/mem': Operation not permitted
1028+0 records in
1028+0 records out
1052672 bytes (1.1 MB) copied, 0.0606602 s, 17.4 MB/s
tedward@hdx16:~$ 
```

---

### Post by bhaverkamp on 2009-12-14
I get same error. There is 3 GB of ram in my system but device only copies first MB. Have seen this before. What needs to be done to get access to all of the RAM?

$ sudo dd if=/dev/mem of=mem.snapshot bs=4k
dd: reading `/dev/mem': Operation not permitted
257+0 records in
257+0 records out
1052672 bytes (1.1 MB) copied, 0.0404052 s, 26.1 MB/s

---

### Post by movieman on 2009-12-14
The kernel appears to be compiled with STRICT_DEVMEM, which restricts access to 'safe' areas of memory.

---

### Post by BkkBonanza on 2009-12-14
Have a look at this page. It mentions a kernal module called fmem that gets around restrictions in 2.6 kernels for dd copying. Never tried it but sounds like it may work.

[http://www.forensicswiki.org/wiki/Tools:Memory_Imaging](http://www.forensicswiki.org/wiki/Tools:Memory_Imaging)

---

