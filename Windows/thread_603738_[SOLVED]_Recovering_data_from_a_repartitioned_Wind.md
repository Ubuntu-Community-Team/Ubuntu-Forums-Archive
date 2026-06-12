---
title: "[SOLVED] Recovering data from a repartitioned Windows drive"
date: 2007-11-05
forum: Windows
---

### Post by aysiu on 2007-11-05
I've Googled around and haven't been able to find a straight answer to this exact question.

A friend (Windows user) accidentally repartitioned her external hard drive. Right after doing that, she tried to use some recovery program (she doesn't remember which one) to get some of the files back. She was able to get pictures back but not music or Word docs. She hasn't touched the drive since.

I thought I might give recovery a try. A few questions, though: [list][*]I know *testdisk* can recovery lost partition tables or deleted partitions, but is it useful for newly created partitions over old partitions? [*]Would *foremost* be a good choice for getting these Word docs back? [*]How likely is it that these Word docs and music are recoverable? Doesn't a repartitioning reformat the drive? I guess since she was able to get pictures back, the files weren't fully deleted, but I haven't done a lot of data recovery so I don't know. [*]Would Knoppix or Ubuntu work better for this? Or does it matter?[/list]

---

### Post by az on 2007-11-05
> **aysiu said:**
> I've Googled around and haven't been able to find a straight answer to this exact question.


*Cracks knuckles*

> **aysiu said:**
> 
I thought I might give recovery a try. A few questions, though: [list][*]I know *testdisk* can recovery lost partition tables or deleted partitions, but is it useful for newly created partitions over old partitions? 

Testdisk (as well as parted - Parted has a rescue function) will scan the disk content for what looks like the beginning of a partition.  That's all it does.  If one new partition was created over the old one, it's pretty much irrelevant.

What is relevant is if the filesystem was formatted.  If the filesystem was formatted, then recovering the filesystem as a whole is not really likely.  Most of the data is still there, though.


> **aysiu said:**
> [*]Would *foremost* be a good choice for getting these Word docs back? 

If the filesystem is gone, yes, foremost or Photorec are two file-carving programs that work very well.  If you use foremost, the "ole" type is for most MS office files and OpenOffice files are just zipped XML files, so use the "zip" type for them.

> **aysiu said:**
> [*]How likely is it that these Word docs and music are recoverable? 

I would bet money on it.  If only one percent of the disk area was erased, then it's likely that small files (like word documents) are not affected.  I only charge my clients if I recover a significant amount of data.  I have yet to not recover most if not all of the data the client wants from a situation like you describe.

Logical file recovery is easy.  When you have hardware problems, it gets difficult.

> **aysiu said:**
> Doesn't a repartitioning reformat the drive? I guess since she was able to get pictures back, the files weren't fully deleted, but I haven't done a lot of data recovery so I don't know. 

Repartitioning only plays around with the partition table.  That being said, many tools do both at the same time.  How was the drive repartitioned?

And even if the drive is formatted, you can still get data back.  A format to ext3 only writes to about one percent of the disk space.  

A "low-leve"l format to NTFS (the one that takes over an hour to complete on a medium-sized disk) will erase data, but not that much and a hard disk is analog.  If you go over the area you just wiped, you will still pick up bits.  If you only formatted once, you probably can still getr 99.9 per cent of your data back.  This would not be so on a digital medium like a memory card or USB disk.

Fortunately, most digital cameras do not do a low-level format.  But I digress...
 

> **aysiu said:**
> 
[*]Would Knoppix or Ubuntu work better for this? Or does it matter?[/list]

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

But, if you have a net connection, it doesn't matter.  So long as you can connect your external drive(s) and make an image of the disk, use whatever.  The Rescue-remix just has all the software;  you don't need to apt-get anything.

---

### Post by aysiu on 2007-11-05
Az, thanks for the quick reply. You've helped a lot.

So as long as I can install Foremost, it doesn't really matter if I'm using Ubuntu or Knoppix. I'll see what happens and post back here when I can get my hands on the external hard drive (it may be a couple more weeks until I see this friend again in person).

---

### Post by aysiu on 2007-11-22
*photorec* worked a charm. ```
sudo apt-get update
sudo apt-get install photorec
sudo photorec
``` Then follow the prompts. Then it retrieves all kinds of files and copies them to your specified location.

---

