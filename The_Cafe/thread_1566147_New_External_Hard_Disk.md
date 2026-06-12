---
title: "New External Hard Disk"
date: 2010-09-02
forum: The Cafe
---

### Post by Khakilang on 2010-09-02
Hi, I just bought a new Seagate 250gb external hard disk for my personal storage.  I want to use it on Ubuntu, Linux, Mac and other OS like BSD, Solaris. Copy and store just about everything, movies, music, photos, document, back up etc.

So what I want to ask is what partition type or File systems should I format in. Currently it say Partition Type : HPFS/NTFS (0x07). I can copy file from Linux and Windows but what about Mac? Does that partition work on Mac OS and other OS like BSD, Solaris? Thanks in advance.
):P

---

### Post by an0dos on 2010-09-02
I think FAT is the lowest common denominator when it comes to file systems.

---

### Post by cammin on 2010-09-02
With the exception of OpenBSD, they should all have r/w access to ntfs after installing the ntfs-3g driver. Most of them have read only access available through in-kernel drivers. 
I know OpenBSD used to have r/o support, but wasn't in the default kernel, It may be now. 
As far as I know, they don't have FUSE, so ntfs-3g isn't available.


If you format the disk to ext2, everything but windows should support it. Windows has an open source driver for it which works for read/write, but I've had it bluescreen when trying to run programs from an ext2 partition. Plus you'll have to add the driver to every Windows PC you want to use the drive on, which might be frowned upon if it's not your computer.


Fat32 is supported by everything, but has rather low limitations in file and partition sizes, among other things.

---

### Post by mips on 2010-09-02
> **cammin said:**
> 
Fat32 is supported by everything, but has rather low limitations in file and partition sizes, among other things.

The 4GB file size limitation can be a real pain.

---

### Post by andrewabc on 2010-09-02
NTFS if you want to use it with other windows machines.

---

### Post by Tracy177 on 2010-09-02
> **Khakilang said:**
> Hi, I just bought a new Seagate 250gb external hard disk for my personal storage.  I want to use it on Ubuntu, Linux, Mac and other OS like BSD, Solaris. Copy and store just about everything, movies, music, photos, document, back up etc.

So what I want to ask is what partition type or File systems should I format in. Currently it say Partition Type : HPFS/NTFS (0x07). I can copy file from Linux and Windows but what about Mac? Does that partition work on Mac OS and other OS like BSD, Solaris? Thanks in advance.
):P


i have two hdd both are ntfs just the partition where ubuntu is installed is different i have two OSes one win 7 other ubuntu 10.04 ubuntu recognise both hdd without problems and i can access both hdd no problem copy etc

---

### Post by Barrucadu on 2010-09-02
FAT32, I'm afraid. I have a NTFS external HDD and discovered, to my horror, that my friend's Mac couldn't write to it when we needed to transfer a load of files.

That was a fun day&#8230;

---

### Post by mips on 2010-09-02
> **Barrucadu said:**
> FAT32, I'm afraid. I have a NTFS external HDD and discovered, to my horror, that my friend's Mac couldn't write to it when we needed to transfer a load of files.

That was a fun day…

OS X requires you to install MacFUSE & ntfs-3g. FAT32 sucks for large file sizes.

---

### Post by Khakilang on 2010-09-03
My brother use Window 7 and my sister use Mac OSX. Occasionally we share files. So does Mac OS recognize NTFS? I know I had no problem with Window 7 but not sure of MAC OS.

---

