---
title: "Dual Booting"
date: 2007-09-01
forum: The Cafe
---

### Post by Gremlinzzz on 2007-09-01
Does dual booting effect ubuntu performance in any negative ways? Does the computer have to take time out for the extra partition .I know it does on boot just wondering on after boot.
:guitar:

---

### Post by popch on 2007-09-01
Once the computer is booted, the dual booting makes no difference. By 'dual booting' I mean the capability to choose from several operating systems when booting.

Since most dual boot installations use partitions on the same physical disk drive, some minor impacts could be considered:

Obviously, there's less disk space available for each OS than there would be if there was only one partition with one OS.

If you make the different partitions needed by each OS not adjacent to each other, the time needed by the disk heads to travel between those partitions can make itself felt.

Unsure: When the disks are powered down (in power saving mode) the heads are brought into a special 'parking' position. I do not know if takes more time when then there are several partitions on the disk. I also do not know if that matters in any real sense.

---

### Post by Lord Illidan on 2007-09-01
No, I don't think it will affect performance, although if the thought bothers you, you can always get an extra harddisk.

---

### Post by Gremlinzzz on 2007-09-01
Thanks for answering i now realize that the question was a little to high tech for most computer users. I also wonder about adding extra hard drives and the effects that has on performance. i have done that in the pass and it didn't make any noticeable difference in the computers performance. but it must do some thing.meaning it is extra hardware.

---

### Post by DoktorSeven on 2007-09-01
None at all.  Extra hard drives/partitions/etc do not negatively impact performance in any significant or noticable way.

---

### Post by rsambuca on 2007-09-01
The only time an extra hard drive can negatively affect performance is if you are using IDE drives, and add the second one as slave.  Because the two drives are now sharing the IDE connection, it can slow things down if copying back and forth between the two.  Also (although unlikely), you could possibly crash your rig if your power supply is too small or a cheap variety that doesn't provide enough juice.

---

### Post by forrestcupp on 2007-09-01
> **rsambuca said:**
> The only time an extra hard drive can negatively affect performance is if you are using IDE drives, and add the second one as slave.  Because the two drives are now sharing the IDE connection, it can slow things down if copying back and forth between the two.  Also (although unlikely), you could possibly crash your rig if your power supply is too small or a cheap variety that doesn't provide enough juice.

And because of that, you may be better off having one large drive with partitions, than to have 2 separate drives with one being a slave.

---

### Post by hidey on 2007-09-01
I dunno I think my Windows installation has started moping after I installed Linux. It hangs on the Welcome screen and then on the desktop for a while during boot up. :)

---

