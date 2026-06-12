---
title: "Reiser4 - The most amazing FS ever!"
date: 2010-11-20
forum: The Cafe
---

### Post by slooksterpsv on 2010-11-20
All,

So I recompiled the kernel tonight and got Reiser4 support and let me tell you it is quick when copying files. Here's the thing, I'm having to recompile cause I accidentally forgot USB support. So here's the thing. Here's a screenshot showing the speed differences between XFS and Reiser4 - I took a large file 1.4GB (VM) and dd'ed it.

Whatcha think? Anyone want a link to compiling the kernel for how I did it?

---

### Post by Spice Weasel on 2010-11-20
Can you defrag Reiser4?

---

### Post by medic2000 on 2010-11-20
Oh my god! I should really ditch Ext4 and try Reiser4!

---

### Post by slooksterpsv on 2010-11-20
> **medic2000 said:**
> Oh my god! I should really ditch Ext4 and try Reiser4!

Compiling the kernel has been the easy party, I, on the other hand, have been complicating things by installing the wrong version of remastersys. I got it, I'm using the right one now and so I'll be switching completely over to it here in about an hour or so.

---

### Post by stefangr1 on 2010-11-20
> **slooksterpsv said:**
> All,
Here's a screenshot showing the speed differences between XFS and Reiser4 - I took a large file 1.4GB (VM) and dd'ed it.

Whatcha think? Anyone want a link to compiling the kernel for how I did it?

How exactly did you perform this test? Are the 73.5 and 30.5MB/s from differently formatted partitions on the same disk? Can you give some info on the type of disks you have?

I'm asking this because 73.5MB/s seems to heigh for a copy to the same disk (on a regular harddisk). Internal read and write speeds are usually somewhere around 100MB/s max, so then you can never get above 50MB/s if you have to both read and write...

At my own system, I'm getting 37.5MB/s from one Samsung Spinpoint F1 1000GB to the same disk, and 64.4MB/s to another disk. 110 MB/s when I copy to /dev/null.

---

### Post by slooksterpsv on 2010-11-20
> **stefangr1 said:**
> How exactly did you perform this test? Are the 73.5 and 30.5MB/s from differently formatted partitions on the same disk? Can you give some info on the type of disks you have?

I'm asking this because 73.5MB/s seems to heigh for a copy to the same disk (on a regular harddisk). Internal read and write speeds are usually somewhere around 100MB/s max, so then you can never get above 50MB/s if you have to both read and write...

At my own system, I'm getting 37.5MB/s from one Samsung Spinpoint F1 1000GB to the same disk, and 64.4MB/s to another disk. 110 MB/s when I copy to /dev/null.

Yes Reiser4, disk to disk copy, did it first so I know it wasn't "cached", that's where the 75MB/s is, Reiser4 is very very very fast.

By the way all I'm having to recompile the kernel again I didn't add support for squashfs which is making it to where I can't create a livecd. So another few hours

---

### Post by stefangr1 on 2010-11-20
> **slooksterpsv said:**
> Yes Reiser4, disk to disk copy, did it first so I know it wasn't "cached", that's where the 75MB/s is, Reiser4 is very very very fast.

Sorry I don't follow you. Do you mean with disk to disk to THE SAME disk, or to A DIFFERENT disk.

Is the only difference between the 30.5 and the 73.5MB/s that the first was on EXT4 and the second on REISER4?

Can you run sudo fdisk -l and post what you get?

Again, I'm not fully convinced about your testing procedure, as you seem to be getting higher transfer speeds than theoretically possible...

---

### Post by Sporkman on 2010-11-20
Interesting stuff in your left Facebook column there...

---

### Post by Spice Weasel on 2010-11-20
Yeah... Next time you take a screenshot, minimise Facebook.

---

### Post by medic2000 on 2010-11-20
Stay on the topic. This is about Reiser4 performance not the facebook.

---

### Post by jdong on 2010-11-20
Unfortunately, use the filesystem for a few weeks then try this again. :)

The performance of reiser4 in my experience rapidly degrades over time, which is what the reiser4 repacker was supposed to resolve but that never seemed to get written.

---

### Post by ukripper on 2010-11-20
> **jdong said:**
> 
The performance of reiser4 in my experience rapidly degrades over time, which is what the reiser4 repacker was supposed to resolve but that never seemed to get written.

^^this

And reiser4 is as good as a dead horse.

---

### Post by Sporkman on 2010-11-20
Btrfs is the future.

---

### Post by Shining Arcanine on 2010-11-20
> **medic2000 said:**
> Stay on the topic. This is about Reiser4 performance not the facebook.

I think that the performance is from its Copy on Write functionality, which means that large sections of the file were not being written at all when you did that in-disk copy.

Copy on Write is used in virtual memory, but doing it on a hard drive brings about issues with fragmentation, which is what jdong mentions in his post.

In that sense, Reiser4 has a great deal in common with NTFS, except Reiser4 derives its fragmentation from copy on write while NTFS derives its fragmentation from laying out files on the disk with no room for files to expand.

---

### Post by linux18 on 2010-11-20
XFS has been benchmarked almost as fast as reiser4 on small files and faster on large files 300MB+, it has defrag capability and superior journaling.

That is why I endorse XFS as the next Pres...ubuntu filesystem!

---

### Post by slooksterpsv on 2010-11-20
> **Sporkman said:**
> Btrfs is the future.

They got a lot of work to do on BTRFS, it's slower than well.... it's the slowest file-system I've used.

---

### Post by czr114 on 2010-11-20
[LEFT]btrfs can't be fscked, and therefore, shouldn't be used in anything but a test environment, even if the slow and unpolished code base wasn't a deterrent.
[/LEFT]

---

### Post by jdong on 2010-11-20
> **Shining Arcanine said:**
> I think that the performance is from its Copy on Write functionality, which means that large sections of the file were not being written at all when you did that in-disk copy.

Copy on Write is used in virtual memory, but doing it on a hard drive brings about issues with fragmentation, which is what jdong mentions in his post.

In that sense, Reiser4 has a great deal in common with NTFS, except Reiser4 derives its fragmentation from copy on write while NTFS derives its fragmentation from laying out files on the disk with no room for files to expand.


Are you sure that you aren't thinking of btrfs? Although Reiser4 uses modified B-Trees (Dancing B-Trees, as Hans called it in his whitepaper), it does not employ copy-on-write techniques, unlike btrfs and ZFS.


The fundamental problem is that BTrees over time, as they are being modified, will lose their spatial/sequential coherency and probably should be reconstructed. Hans noted that there was a way, in the reiser4 tree design, that a sequence of online tree modification operations can be used to achieve the same effect as destroying and rebuilding all the trees, and this was the technique in the online repacker that he proposed.

---

