---
title: "Which file system to use?"
date: 2009-08-21
forum: The Cafe
---

### Post by praveesh on 2009-08-21
The kUbuntu installed inside windows in the ntfs partition is faster than that installed independly on an ext4 partition in my desktop computer . I think the performance improvement is due to the ntfs file system. This introduced in me a doubt. Which file system shall a use for my linux installation? Ext4 ?ext3? Xfs? Or any other? My goal is to get the maximum performance. What do you think? Which is your suggested file system?why . Everything will have it's demerit too. So please tell the drawbacks of the suggested file system too. Thanks. (do any of you use a file system different from the ext?)

---

### Post by Firestem4 on 2009-08-21
I am not an expert on linux filesystems so don't take my word as such, however here are my thoughts on linux file systems.

Ext3 and its sucessor Ext4 are great all-purpose filesystems with a good balance between performance, stability, redundancy, and scalability. Unless you have a specific NEED for one of the other file systems ext3/4 will serve most of your needs fairly well.

Having said that there are many alternatives. XFS I *do* know for a fact has a huge performance boost handling very large files. (Creation, modification, deletion, etc). Its very stable too. This would be something you should look into if for instance you had a lot of raw data (video stock for instance).

The reason NTFS is fast (or can be) is because the file system does not care where its writing data. It literally writes it where it finds space. Depending on levels of fragmentation this can either cause an increase or decrease in performance. Also however, Windows is optimized for the NTFS file system which gives Windowes a performance increase under NTFS.

Linux file systems are designed to avoid writing files out-of-contigous order and appropriates the needed amount of contigious disk-space before writing. This helps in the long run because linux file system do not (or rarely) suffer from file-fragmenation.

Most other Linux file systems follow the same design. 

My recommendation would be to use EXT4. It is officially stable as of 9.04 I believe and it has (varying) degrees of performance over ext3.

---

### Post by HoKaze on 2009-08-21
I'm probably even less knowledgable on the subject than the previous poster (who summed it up pretty nicely) but I'd personally go with ext3 over ext4 for the simple matter of it having been supported longer and being more stable. I advise against NTFS myself, unless you want to have to defrag like in windows :P

---

### Post by praveesh on 2009-08-21
I don't use ntfs for installing Ubuntu/kUbuntu. But for installing inside windows, the file system used will be ntfs. I can't change it.

---

### Post by Firestem4 on 2009-08-21
> **praveesh said:**
> I don't use ntfs for installing Ubuntu/kUbuntu. But for installing inside windows, the file system used will be ntfs. I can't change it.

If you are going to do a Wubi install then you have no choice but to use NTFS. However if you instead dual-boot you can choose what file systems to use.

---

### Post by cascade9 on 2009-08-21
> **praveesh said:**
> The kUbuntu installed inside windows in the ntfs partition is faster than that installed independly on an ext4 partition in my desktop computer . I think the performance improvement is due to the ntfs file system. This introduced in me a doubt. Which file system shall a use for my linux installation? Ext4 ?ext3? Xfs? Or any other? My goal is to get the maximum performance. What do you think? Which is your suggested file system?why . Everything will have it's demerit too. So please tell the drawbacks of the suggested file system too. Thanks. (do any of you use a file system different from the ext?)

I would guess that your windows partition is right at the beginning of the drive (thats typically where it is unless you play with partitions). If your kubuntu is at the end of the drive, hdd read speeds could be as much as 50% slower. 

Again, I'm not an expert on linux FS, but generally-

RFS- Fast, less protection against file corruption
EXT3/4- Slightly slower than RFS, but better data protection.
XFS- Best for large partitons with lots of large files. 

Heres some benchmarks-
[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1)

Personally, I wouldnt use RFS, I dont have big enough files for XFS to be worth it, I'm currently using EXT3 (I'll wait for EXT4 to mature a bit more before I use it) 

Theres also other options, like more obscure linux FS, eg OCFS, GFS, Google File system, etc, and nonlinux FS, eg ZFS (last I checked that was though fuse only). But generally, RFS/EXT/XFS will do what you want it to. At least untill btrfs comes out as stable :D

---

### Post by hessiess on 2009-08-21
Currently ext3 is the most stable general filsystem, ext4 is still very new. Keep an eye on ZFS.

---

### Post by &#32 Greg on 2009-08-21
I use JFS. It's stable, as well as very good for a quick fsck.

---

### Post by Stan_1936 on 2009-08-21
> **cascade9 said:**
> ...
RFS- Fast, less protection against file corruption....

Is RFS available, as a possible filesystem, in Debian(Lenny)?

---

### Post by hoppipolla on 2009-08-21
I love ext4. But XFS looks interesting too :)

---

### Post by cascade9 on 2009-08-21
> **Stan_1936 said:**
> Is RFS available, as a possible filesystem, in Debian(Lenny)?

Yes. But I'm not a big fan of RFS4, and I cant recall if RS is an option from boot or if you need to post-install it. 

Just so you know-

> ReiserFS had a problem with very fast filesystem aging when compared to other filesystems - in several usage scenarios filesystem performance lowered dramatically with time. Because ReiserFS still uses the [Big Kernel Lock]("http://en.wikipedia.org/wiki/Giant_lock") (BKL) — a global kernel-wide lock — in some places, it does not scale very well for systems with multiple cores, as the critical code parts are only ever executed by one core at a time. 

[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)

> Hans Reiser was convicted of [murder]("http://en.wikipedia.org/wiki/Murder") on April 28th, 2008, leaving the future of Reiser4 uncertain. After his arrest, employees of Namesys assured they would continue to work and that the events would not slow down the software development in the immediate future. In order to afford increasing legal fees, Hans Reiser announced on December 21, 2006 that he was going to sell Namesys;[]("http://en.wikipedia.org/wiki/Reiser4#cite_note-6") as of March 26, 2008, it has not been sold, although the website is unavailable. In [January 2008]("http://en.wikipedia.org/wiki/January_2008"), Edward Shishkin, an employee of and programmer for Namesys, was quoted in a CNET interview saying that "Commercial activity of Namesys has stopped." Shishkin and others continued the development of Reiser4,[]("http://en.wikipedia.org/wiki/Reiser4#cite_note-7") making source code available from Shishkin's web site,[]("http://en.wikipedia.org/wiki/Reiser4#cite_note-8") later relocated to [kernel.org]("http://en.wikipedia.org/wiki/Kernel.org").[]("http://en.wikipedia.org/wiki/Reiser4#cite_note-9")

Although kernel developer [Theodore Ts'o]("http://en.wikipedia.org/wiki/Theodore_Ts%27o") has suggested [btrfs]("http://en.wikipedia.org/wiki/Btrfs") as an alternative for those interested in the design ideas of Reiser4,[]("http://en.wikipedia.org/wiki/Reiser4#cite_note-10") Reiser4 development still continues,[]("http://en.wikipedia.org/wiki/Reiser4#cite_note-11") delivering patches via kernel.org.[]("http://en.wikipedia.org/wiki/Reiser4#cite_note-12")

[http://en.wikipedia.org/wiki/Reiser4](http://en.wikipedia.org/wiki/Reiser4)

Yeah, RFS is fast, but its not getting much development anymore, and btrfs should be better option, when it comes out.

---

### Post by northwestuntu on 2009-08-21
> **hoppipolla said:**
> I love ext4. But XFS looks interesting too :)

i don't trust ext4.  i've had some bad errors on systems i have installed that on. so bad where i had to reformat.  im sticking with ext3 for a while.

---

### Post by cariboo on 2009-08-21
If you don't trust ext4, and you want speed try xfs, it is almost as fast as ext4, but has been around for years.

---

### Post by SunnyRabbiera on 2009-08-21
Personally I think EXT3 is the best FS for now, its stable, its reliable and it is quite fast depending on the computer it is on.
On my machines EXT3 has performed far greater then NTFS

---

### Post by kk0sse54 on 2009-08-21
For linux I would most definitely choose JFS. On *BSD , ZFS :)

---

### Post by praveesh on 2009-08-21
Oh , my linux partition and the swap are at the end of the disk. When installed with wuby , it is installed in the cdrive , which is at the beginning. That may be the reason for the performance difference. I assume that as the linux file system approaches the beginning of the drive, the speed will be increased. My C drive is 30 Gb . Shall I reduce it to 15 Gb and use the rest of the part as ext4 for making the linux partition more close to the beginning. What do you think? How much sizi shall I allocate for the Cdrive?

---

### Post by cascade9 on 2009-08-22
I probably wouldnt resize C:. Sure, its do-able, but theres always the chance of data problems.

---

### Post by Jimleko211 on 2009-08-22
NFTS isn't any faster than ext3/4.  Slower, in fact, as time goes on.  The reason why it installed faster for you was because it didn't have to repartition, it installed into an existing partition.

---

