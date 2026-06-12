---
title: "Why can't i have more than 4 primary partitions."
date: 2009-02-16
forum: The Cafe
---

### Post by dragos240 on 2009-02-16
I was just wondering, why can't i have more than 4 primary partitions.... It just doesn't make sense to me. Is there a reason? I mean, i know i can have up to 64 logical partitions, but why not 5 or 6 primary?

---

### Post by wilbbe01 on 2009-02-16
> I was just wondering, why can't i have more than 4 primary partitions.... It just doesn't make sense to me. Is there a reason? I mean, i know i can have up to 64 logical partitions, but why not 5 or 6 primary?

That is all the MBR has space for/is structured to hold.

---

### Post by cardinals_fan on 2009-02-16
This has to do with the MBR structure.  I'll dig up some links...

---

### Post by SunnyRabbiera on 2009-02-16
Its a limitation even in the most modern hard drives, its not any df\ault of any OS but I know it has something to do with the boot record.

---

### Post by dragos240 on 2009-02-16
is there any way you could change this to make it able to have more than 4? Or is t built into the read only memory.

---

### Post by cdtech on 2009-02-16
Here's some reading material:
[http://www.lissot.net/partition/partition-03.html](http://www.lissot.net/partition/partition-03.html)
[http://www.bleepingcomputer.com/tutorials/tutorial115.html](http://www.bleepingcomputer.com/tutorials/tutorial115.html)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by cardinals_fan on 2009-02-16
Why do you need more than four?  BSD systems usually require a primary, but do you need to boot that many of them?

---

### Post by dragos240 on 2009-02-16
> **cdtech said:**
> Here's some reading material:
[http://www.lissot.net/partition/partition-03.html](http://www.lissot.net/partition/partition-03.html)
[http://www.bleepingcomputer.com/tutorials/tutorial115.html](http://www.bleepingcomputer.com/tutorials/tutorial115.html)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Huh, it said that Intel based systems were just limited... what about amd?

---

### Post by dragos240 on 2009-02-16
> **cardinals_fan said:**
> Why do you need more than four?  BSD systems usually require a primary, but do you need to boot that many of them?

No, i was just wondering, and i was about to request a picture of beastie being stabed by tux, no just kidding.

---

### Post by cardinals_fan on 2009-02-16
> **dragos240 said:**
> No, i was just wondering, and i was about to request a picture of beastie being stabed by tux, no just kidding.
"Fred is one mean looking insect, the go-lucky demon and fat penguin are TOAST!  Well, maybe not, but Fred is still one mean looking insect!"
- the DragonFlyBSD Mascot page

---

### Post by kk0sse54 on 2009-02-16
> **dragos240 said:**
> No, i was just wondering, and i was about to request a picture of beastie being stabed by tux, no just kidding.

I tried to find that picture but could only find the other way around.

---

### Post by damis648 on 2009-02-16
Hm... do GPT (GUID Partitioned) disks have the same limitation?

---

### Post by cdtech on 2009-02-16
> **dragos240 said:**
> Huh, it said that Intel based systems were just limited... what about amd?

> By convention, there are exactly four primary partition table entries in the MBR Partition Table scheme, although some DOS operating systems did extend this to five (PTS-DOS)[16] or even eight (AST or NEC DOS)[17][18] entries. Both the partition length and partition start address are stored as 32-bit quantities. Because the block size is 512 bytes, this implies that neither the maximum size of a partition nor the maximum start address (both in bytes) can exceed 232 × 512 bytes, or 2 TiB. Alleviating this capacity limitation is one of the prime motivations for the development of the GUID Partition Table (GPT).

It's a MBR morals issue. See this link:
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by dragos240 on 2009-02-16
> **cardinals_fan said:**
> "Fred is one mean looking insect, the go-lucky demon and fat penguin are TOAST!  Well, maybe not, but Fred is still one mean looking insect!"
- the DragonFlyBSD Mascot page

He doesn't look so mean XD:
[IMG]http://www.dragonflybsd.org/images/mascot.jpg[/IMG]




> 
I tried to find that picture but could only find the other way around.

Same here >.<

---

### Post by kk0sse54 on 2009-02-16
> He doesn't look so mean XD:
You were saying :twisted:

[ATTACH]103573[/ATTACH]

---

### Post by dragos240 on 2009-02-16
> **C!oud said:**
> You were saying :twisted:

[ATTACH]103573[/ATTACH]


He was talking about the BSD dragonfly not beastie.

Poor tux, [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

