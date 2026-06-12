---
title: "Defragger: What do you think...."
date: 2005-04-08
forum: The Cafe
---

### Post by Perfect Storm on 2005-04-08
[http://www.oo-software.com/en/products/oodlinux/index.html](http://www.oo-software.com/en/products/oodlinux/index.html)

Though I know linux doesn't use defrag, so why build a defragger for linux?

---

### Post by TjaBBe on 2005-04-08
[QUOTE=Artificial Intelligence][http://www.oo-software.com/en/products/oodlinux/index.html](http://www.oo-software.com/en/products/oodlinux/index.html)

Though I know linux doesn't use defrag, so why build a defragger for linux?[/QUOTE]
As far as I know Linux filesystems don't even NEED to be defragged. Obviously this is someone with too much spare time ;).

---

### Post by bigzak on 2005-04-08
Looks like a commercial (paid) product. I guess they'll be relying on the fact that defragmentation of drives is ingrained into the public consience that people will buy it because "disks need to be defragmented to speed them up".

It's basically cashing in on MS's failings :(

---

### Post by Ubunted on 2005-04-08
Kinda reminds me of all the "RAM Defrag" placebo programs out there. Useless, but you can bet someone's going to sink their dough into it.

---

### Post by seven on 2005-04-08
Defrag is not needed at all for linux AFAIK, just bored people with free time  :roll:

---

### Post by bigzak on 2005-04-08
[QUOTE=Ubunted]Kinda reminds me of all the "RAM Defrag" placebo programs out there. Useless, but you can bet someone's going to sink their dough into it.[/QUOTE]

Yes. A mate of mine actually paid good money for a 'RAM doubler' that was supposed to compress RAM on the fly, drivespace style. I'm not sure if it was a total fraud (which was raised as a possiblity) but the machine benchmarked significantly slower than without it, and available RAM was, well, almost exactly the same as before.

Of course, he swore blind that it made a VAST improvement, far more than just spending the same amount on actual RAM would have provided.

---

### Post by Perfect Storm on 2005-04-08
I think I'm gonna E-mail them and hear what they have to say.... I really like to know their reason why linux users should invest money in it, though the beta version is free.

---

### Post by Sam on 2005-04-08
I've heard somewhere that an almost-full disc could start being fragged.

---

### Post by HungSquirrel on 2005-04-08
I've never understood why Linux partitions don't need to be defragged.  How exactly does it work?

---

### Post by TravisNewman on 2005-04-08
I'd love to know that myself! I know the filesystem is a lot more robust and everything, but you'd THINK there'd be some fragmentation.

---

### Post by mike998 on 2005-04-08
I'm not 100% sure and could be completely wrong, but I belive it's something to do with the fact that the filesystem is a journalled filesystem, and information is written to disk to a type of scratchpad area, sorted and then written to disk "permanently".

Having said that, old non-journalled ext3 filesystems didnt need to be defragged either.

Hmmm... I wonder if there is a utility to see my file allocation?  I have some really big files on my HDD at home...

---

### Post by HungSquirrel on 2005-04-08
Ext3 is journaled.

NTFS is journaled IIRC and it needs monthly defragging.

---

### Post by Glanz on 2005-04-08
[QUOTE=mike998]I'm not 100% sure and could be completely wrong, but I belive it's something to do with the fact that the filesystem is a journalled filesystem, and information is written to disk to a type of scratchpad area, sorted and then written to disk "permanently".

Having said that, old non-journalled ext3 filesystems didnt need to be defragged either.

Hmmm... I wonder if there is a utility to see my file allocation?  I have some really big files on my HDD at home...[/QUOTE]
 In general, the allocation policy for JFS tries to maximize contiguous allocation by allocating a minimum number of extents, with each extent as large and contiguous as possible. This allows for large I/O transfer, resulting in improved performance. However, in special cases this is not always possible. For example, copy-on-write clones of a segment will cause a contiguous extent to be partitioned into a sequence of smaller contiguous extents. Another case is restriction of extent size. For example, the extent size is restricted for compressed files since JFS must read the entire extent into memory and decompress it. JFS has a limited amount of memory available, so it must ensure that it will have enough room for the decompressed extent.

 A defragmentation utility is provided to reduce external fragmentation, which occurs from dynamic allocation/deallocation of variable-size extents. This allocation and deallocation can result in disconnected variable size free extents all over the aggregate. The defragmentation utility will coalesce multiple small free extents into single larger extents.

---

### Post by jdong on 2005-04-08
It's been 2 weeks or so since I've defragged my 200GB XFS partition:

```

jdong@delta:~$ time sudo xfs_fsr
xfs_fsr -m /etc/mtab -t 7200 -f /var/tmp/.fsrlast_xfs ...
/ start inode=0
/ start inode=0
/ start inode=0
/ start inode=0
/ start inode=0
/ start inode=0
/ start inode=0
/ start inode=0
/ start inode=0
/ start inode=0
Completed all 10 passes

real	0m18.332s
user	0m0.503s
sys	 0m1.788s
jdong@delta:~$ 


```

WOW, that took a whopping 18 seconds to defrag.... (BTW, XFS also resists fragmentation)

---

### Post by az on 2005-04-08
Right, EXT2 is not journaled and resists fragmentation as well as Ext3.  The journaling in Ext3 is just a reconrd-keeping practice added on top.  You can mount your ext3 filesystem as ext2, if you want.  Fragmentation is minimized on these filesystems, but not non-existant.

It does not lead to lock-ups or instability like it does on Windows systems.

So, as far as I know, it is present to a lesser degree, and is a lot less of a problem for ext2 and ext3 filesystems.

The everyday linux user does not have to worry about it.

---

### Post by jdong on 2005-04-08
If you fill your disk to the 95%+ mark, performance will degrade rapidly, and fragmentation will also get out of control like in Windows.

It's generally NOT a good idea to fill hard disks to the brim, anyway.

---

### Post by mike998 on 2005-04-08
I stand corrected.
As to the above about drives becoming more than 95% filled...
```
[root@ariadne root]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              18G   15G  2.4G  86% /
/dev/hda1              99M   14M   79M  15% /boot
none                   89M     0   89M   0% /dev/shm
``` 
I guess I gotta worry about my poor server....

---

### Post by jdong on 2005-04-08
I'd recommend separating the user data from the system files. It's OK if /home gets a bit fragged up. When /var and /usr get fragged, you'll suffer a huge performance hit.

---

### Post by DJ_Max on 2005-04-08
To pretty much reiterate what azz said, disk fragmentation is a common problem with the DOS FAT file system(s). Reason being a number of issues, mainly how it handles files, and uses the registery.

Most Unix(including OS X) won't have a problem. For the rare ocasions, do something similar to what jdong did.

---

### Post by jerome bettis on 2005-04-09
well i was going to explain this whole internal / external fragmentation thing.  but i'm getting a little too drunk and it's getting a little too complicated.  i'll post that sometime tommorow.

for now i'll leave you with a quote from the book that explains all of this stuff:

"In an experiment to see if Windows NT file usage was appreciably different from UNIX file usage, [some smart guy] made measurements on files at Cornell University.  He observed that NT file usage is more complicated than on UNIX.  He wrote:

[quote=smart guy]When we type a few characters in the notepad text editor, saving this to  a file will trigger 26 system calls, including three failed open attempts, 1 file overwrite, and 4 additional open and close sequences."[/quote]

LOL

---

### Post by Ubunted on 2005-04-09
The innards of MS at their best I suppose. Amazing.

---

### Post by jdong on 2005-04-10
WOW, that's gonna be my new sig.

---

### Post by poofyhairguy on 2005-04-10
[QUOTE=jdong]If you fill your disk to the 95%+ mark, performance will degrade rapidly, and fragmentation will also get out of control like in Windows.

[/QUOTE]


Oooops. time to buy a new hard disk...

---

### Post by bigzak on 2005-04-11
[QUOTE=panickedthumb]I'd love to know that myself! I know the filesystem is a lot more robust and everything, but you'd THINK there'd be some fragmentation.[/QUOTE]

The output of fsck will tell you how fragmented, or 'non-contiguous', the file system is. When I obliterated my Slackware ext3 filesystem of 2 years+ to put Ubuntu on, the last fsck said it was 1.01% non-contigous. A FAT partition gets more fragmented that than in 2 days!

---

### Post by jdong on 2005-04-11
As I've said before, the only case where ext3/XFS get fragmented is when you fill the disk up to the brim.

---

