---
title: "ext4 filesystem released"
date: 2006-10-10
forum: The Cafe
---

### Post by plb on 2006-10-10
[http://www.kr.kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.19-rc1/2.6.19-rc1-mm1/announce.txt](http://www.kr.kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.19-rc1/2.6.19-rc1-mm1/announce.txt)
[http://digg.com/linux_unix/The_ext4_filesystem_has_been_released](http://digg.com/linux_unix/The_ext4_filesystem_has_been_released)

---

### Post by BOBSONATOR on 2006-10-10
Will this be included in edgy?

---

### Post by maniacmusician on 2006-10-10
nah, way too late. i'm sure there will be a way for people to implement it in edgy, if they wish to do so. but it probably wont be a default till it gets *extensively* tested by lots of people.

---

### Post by PriceChild on 2006-10-11
Wouldn't you just need to compile the latest kernel to be able to use/create ext4 systems? Correct me if i'm wrong!

---

### Post by asimon on 2006-10-11
> **PriceChild said:**
> Wouldn't you just need to compile the latest kernel to be able to use/create ext4 systems? Correct me if i'm wrong!
Yes, you need a kernel version 2.6.19-rc1 or later and the latest [e2fsprogs](ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs-interim/), just as the announcement says.

---

### Post by grizzly on 2006-10-11
Hey will this implement some sort of undelete/recycle bin or something?

---

### Post by Rhapsody on 2006-10-11
> **grizzly said:**
> Hey will this implement some sort of undelete/recycle bin or something?
I think 'Recycle Bin-like' functionality is something the OS provides (I certainly have one here with the KDE Wastebin). It's not like the Recycle Bin is an integral function of FAT16/32, it was Microsoft operating systems that implemented it (of course the idea was plagarized from Apple, where Microsoft get most of their 'innovation'). As for undelete, according to Wikpedia's ext3 article:

"Unlike ext2, ext3 zeroes out block pointers in the inodes of deleted files. It does to simplify read-write access to the filesystem when the journal is being replayed after an unclean mount. This, however, effectively prevents files from being undeleted. The user's only recourse is to grep the hard drive for data known to signal the start and end of the file. This provides slightly more secure deletion than ext2, which can be either an advantage or a disadvantage."

I don't think ext4 has been changed in this respect, so it'll be the same there. This isn't anything serious though. Just *think* for a second when you're confirming deletion of a file.

---

### Post by grizzly on 2006-10-11
> I don't think ext4 has been changed in this respect, so it'll be the same there. This isn't anything serious though. Just think for a second when you're confirming deletion of a file.
Have you never rm'ed a file by mistake?????? besides the wrong file can always  be deleted  by a lil extra tab, similar spelling , or by another  gazillion reasons why this can happen etc 

Currently I use (like most ppl i guess) : 
alias rms=rm
alias rm=mv ~/.trash/

which works, but..

---

### Post by Nonno Bassotto on 2006-10-11
> **Rhapsody said:**
> I think 'Recycle Bin-like' functionality is something the OS provides (I certainly have one here with the KDE Wastebin). It's not like the Recycle Bin is an integral function of FAT16/32, it was Microsoft operating systems that implemented it (of course the idea was plagarized from Apple, where Microsoft get most of their 'innovation'). As for undelete, according to Wikpedia's ext3 article:

"Unlike ext2, ext3 zeroes out block pointers in the inodes of deleted files. It does to simplify read-write access to the filesystem when the journal is being replayed after an unclean mount. This, however, effectively prevents files from being undeleted. The user's only recourse is to grep the hard drive for data known to signal the start and end of the file. This provides slightly more secure deletion than ext2, which can be either an advantage or a disadvantage."

I don't think ext4 has been changed in this respect, so it'll be the same there. This isn't anything serious though. Just *think* for a second when you're confirming deletion of a file.

I think he refers to the fact that the recycle bin currently does not support the possibility to restore the file to the original location.

---

### Post by prizrak on 2006-10-11
Kinda interesting but I wonder what the benefits are. Hopefully speed would be one of them, since lets face it for home users data integrity and availability is kind of an afterthought.

---

### Post by chaosgeisterchen on 2006-10-11
It's still interesting that the ext4-Filesystem gets included into Kernel even if it's not even near final stage but Reiser4 is kept out of it for widespread testing - and it's been tested for more time now.

I can understand that Hans Reiser is angry about that.

---

### Post by prizrak on 2006-10-11
> **chaosgeisterchen said:**
> It's still interesting that the ext4-Filesystem gets included into Kernel even if it's not even near final stage but Reiser4 is kept out of it for widespread testing - and it's been tested for more time now.

I can understand that Hans Reiser is angry about that.

Well Reiser was always pretty quirky even the previous well tested version of it had some issues. Reiser is also not nearly as popular as ext, no to mention that ext4 is basically an improvement on an already solid ext2/3 as opposed to a totally new product that reiser4 is (AFAIK it's pretty much completely rewritten). There have been a move towards ext lately actually. XFS has been dropped completely, I think JFS as well and alot of distros default to ext.

---

### Post by chaosgeisterchen on 2006-10-11
Hmh. I heard that Reiser4 would be the fastest and most performant FS available at the moment :)

---

### Post by prizrak on 2006-10-11
> **chaosgeisterchen said:**
> Hmh. I heard that Reiser4 would be the fastest and most performant FS available at the moment :)

It may just be, but how stable is it? You need both in business setting and XFS is actually better than either ext or reiser. Home users don't care much about either, you won't see noticeable speed differences in desktop applications. Also I don't believe ReiserFS was ever part of the kernel, I think it always needed a module installed. Ext was always the one that is in the kernel itself. (Now I'm not sure about that, I'm speculating on the basis that there is a mk2fs command to create ext partitions and reiser is created with mkfs.reiser command)

---

