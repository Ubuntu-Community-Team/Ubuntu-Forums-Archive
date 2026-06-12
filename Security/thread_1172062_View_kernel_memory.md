---
title: "View kernel memory"
date: 2009-05-28
forum: Security
---

### Post by Tyconic on 2009-05-28
Hi folks,

Wondering if its possible to get a real time view of the kernel image in memory. For reference I've tried using kmem...

```

$ sudo cat kmem
cat: kmem: No such device or address

```

without success (is it disabled in Jaunty??). 

Thnaks in advance,
-t

---

### Post by The Tronyx on 2009-05-28
I believe you are looking for /dev/kmem.

The best you can do is dump all physical memory.  I spent a bit of time trying to figure out a way to dump all physical memory to a flat text file screwing around with LD_Preloads and other stuff but I found that dd works best.
```

dd if=/dev/mem of=~/memdump.txt

```
You might be able to just use /dev/kmem but I am not sure about that as I am not currently on or around an Ubuntu install.

Lastly, if you are looking for a little more information from a code perspective, perhaps the attached may help.  If you compile and run, you can dump physical memory but as noted previously, I prefer the dd method for /dev/mem.  This may not be exactly what you need, but it might push you in the right direction.

---

### Post by Tyconic on 2009-05-28
Thanks for the tips :) /dev/kmem was indeed my target. 

My only concern about using /dev/mem is that I'm after kernel virtual memory addresses. Something along the lines of what's in /boot/System.map I'm doing some noobish module programming and I'd like to see what my code is doing to the operation of the kernel.

FYI, digging a little deeper, you can find /dev/kmem no longer supported on ubuntu... for instance [https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/354221](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/354221)

They are getting tooo suspicious... before you know it all the cool toys will be gone and we'll be left staring at a neon fish :)

---

### Post by Tyconic on 2009-05-28
I guess my problem is now to find which areas of physical memory map to the kernel, but I have no idea how to approach this problem. Is there some kind of paging table that will tell me whether a particular area of physical memory is part of the kernel? Or better yet, given a kernel address, which region of physical memory I should go seek out?

---

### Post by The Tronyx on 2009-05-28
> **Tyconic said:**
> I guess my problem is now to find which areas of physical memory map to the kernel, but I have no idea how to approach this problem. Is there some kind of paging table that will tell me whether a particular area of physical memory is part of the kernel? Or better yet, given a kernel address, which region of physical memory I should go seek out?

I like your idea about the neon fish more.

This is some kind of black magic...I don't think it is going to happen the way you want it to.  The ability to explicitly check and discern what portions of physical memory or what memory addresses are responsible for kernel functions, would be a fairly significant security issue.  By major I mean that any kind of exploit or vulnerability that divulges kernel memory is pretty serious, you are asking for a way to automagically do this which I don't believe is possible by design.

To clarify, this wouldn't be so difficult if you knew what it was you wanted to find the memory address(es) of, but you really have no clue what you are looking for.  On this note, the issue is not finding the memory addresses or memory space allocated to process X but rather finding memory data of content Y, content Y being the kernel and its related functions in their entirety which isn't really...doable.  There is also the issue of noncontiguous memory which would serve to complicate things quite a bit.

I think a lot of what you are looking for is going to be in /proc but I don't believe you will find it the way you are wanting to see it.

I have an awkward sentence structure, hope what I said makes sense.

I would also like to say that this is a great question.  Must have to do with being from the best city in the U.S. ;)

---

