---
title: "ext4 - when will it stablize ?"
date: 2009-07-18
forum: Server Platforms
---

### Post by abraham.varricatt on 2009-07-18
I've been searching in the forums to decide if I should use ext3 or ext4 on a production server. Wanting stability and reliability, I've decided to stick with ext3.

But the stability issues reported in ext4 makes me wonder, how does it get fixed ? Especially, since ext4 has already been released ?

I mean, this is not like patching source-code is it? You can't just say "lets rearrange the bit-order on the hard disk to fix problem Z". Doing something like that will naturally break older ext4 implementations !!

I'm familiar with how patches work for a software product, but for a file-system definition, ... it just doesn't make sense.

What am I missing here ? :confused:

---

### Post by ibutho on 2009-07-18
The improvements and bug fixing are made in the kernel because ext4 is developed by a group of Linux kernel devs. If you upgrade your kernel (or patch your old one) to the latest versions, then you get access to the various fixes.

---

### Post by abraham.varricatt on 2009-07-18
Hmm... thats interesting information for me.

But, what I was asking was a bit different. We know that ext3 and NTFS are directly incompatible with each other, right ? And the reason is because both write bits on the hard-disk in a different manner.

So, in that way, since the arrangement of the bits in ext4 is finalized, what is left to fix? At best, we can twiddle with the way in the which the stuff is written, but is that the cause of all the data-losses with ext4 ?

Am I getting clearer, or more confusing ?

---

### Post by ian dobson on 2009-07-19
Hi,

The last set of patches to ext4 change the order that the data/meta data is written to the disk making it work more like ext3 by default.

Think about this:-
The file system has to write the actual data to the disk at some point and write the directory information at some point. Which one should it write first?

1) If you say user data then directory, what happends if the system crashes between writing the user data and the directory structure? You'll still have the old user data and space on the disk that is not allocated to anything even through it contains the user data you've just written.

2) If you say directory then user data, what happends if the system crashes between writing the directory structure and the user data? The old user data won't be accessable as the meta data/directory structure points to the disk space that has been allocated for the new user data but not yet written.

ext4 used method 2 until the problems were found with the X11 system expecting the data to be written according to method 1. 

One way to get around this problem is to use the sync command which flushes are data from the cache to the disk but thats not a "nice" solution (It takes time, forces the kernel to write the data now rather than when it thinks it's OK to do, harddisks are being accessed more often).

Regards
Ian Dobson

---

### Post by renkinjutsu on 2009-07-19
if you look at some of the guides on how to convert from ext3 to ext4 on your existing setup.. they'll all tell you that the advantages of ext4 will only be seen in the new files you create.. I think the ext4 patches work the same way in that it only affects the newer files while the old files are still accessible.

---

### Post by theozzlives on 2009-07-19
It seems pretty stable to me, I have ext4 on all my machines. From what I read the problem people have been experiencing is in the journaling. Losing data during a power failure or system crash. I've experienced both and (to my knowledge) haven't lost any data.

---

### Post by binbash on 2009-07-19
> **renkinjutsu said:**
> if you look at some of the guides on how to convert from ext3 to ext4 on your existing setup.. they'll all tell you that the advantages of ext4 will only be seen in the new files you create.. I think the ext4 patches work the same way in that it only affects the newer files while the old files are still accessible.

Yup this is right

---

### Post by abraham.varricatt on 2009-07-19
Thanks for all the info guys. Still, for my production server, I think I'll stick with ext3. I'll wait some more before I consider ext4.

In the meantime, I think I'll experiment it (ext4) on some desktops I have around.

---

### Post by juancarlospaco on 2009-07-19
EXT4 is stable. I don't know why people says that isn't. :)

---

