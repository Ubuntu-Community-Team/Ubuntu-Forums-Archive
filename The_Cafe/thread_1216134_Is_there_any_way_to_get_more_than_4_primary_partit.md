---
title: "Is there any way to get more than 4 primary partitions?"
date: 2009-07-17
forum: The Cafe
---

### Post by dragos240 on 2009-07-17
Just curious. Is there?

---

### Post by bodhi.zazen on 2009-07-17
No

You may have an extended partition with multiple logical partitions.

If needed : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by lisati on 2009-07-17
> **dragos240 said:**
> Just curious. Is there?

I don't think so, partly for historical reasons.
Have a look here: [http://en.wikipedia.org/wiki/Disk_partitioning#PC_BIOS_partition_types](http://en.wikipedia.org/wiki/Disk_partitioning#PC_BIOS_partition_types)

---

### Post by Bucky Ball on 2009-07-17
Nope, but Linux doesn't need to be on a primary partition if that helps, only MS.

You can install Ubuntu to a logical inside an extended partition, and you can have heaps of logicals!

---

### Post by dragos240 on 2009-07-17
So you couldn't get more than 4 primary partitions if you wanted to, like using advanced modding, of your system, etc.

---

### Post by Bucky Ball on 2009-07-17
It don't work that way.

---

### Post by gn2 on 2009-07-18
Yes, it's really easy.

Just fit more hard drives.

---

### Post by Bucky Ball on 2009-07-18
> **gn2 said:**
> Yes, it's really easy.

Just fit more hard drives.

Good point. There is that. :-k

---

### Post by dragos240 on 2009-07-18
Change of question. How many hard drives can you have?

---

### Post by Bucky Ball on 2009-07-18
Depends on the motherboard. An IDE cable can take two devices. There used to be two cables=four devices. More usual now, with the advent of SATA, one.

SATA is usually four plugs on the board.

External hard drive numbers depend on amount of USB, Firewire and eSATA ports. I guess if you used a hub and POWERED external hard drive enclosures (not powered by the rails of the computer), you could achieve quite a number. 

Before attempting this experiment, make sure you can afford it when you reach breaking point!

---

### Post by ddrichardson on 2009-07-18
> **Bucky Ball said:**
> Depends on the motherboard. An IDE cable can take two devices. There used to be two cables=four devices. More usual now, with the advent of SATA, one.
While true of SATA150, SATA300 and eSATA can have 15 per line with a port multiplier.

---

### Post by SuperSonic4 on 2009-07-18
Do you know where I would get one of these (preferably from the UK - Sterling needs to be stronger before I start importing again XD). I have two eSATA ports already.

I can directly connect 6 sATA **devices** onto mine - this could be either hard drives or optical drives

---

### Post by Stan% on 2009-07-18
BootIt NG is a boot/partition manager, that has a setting to allow as many primaries as you want. If you install it, it will replace your current boot manager.

You can install it free but donate if you can. (at least it used to be free, I haven't used it in some time)

[http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm)

Wait, see what others have to say about using it with Linux.

---

### Post by ddrichardson on 2009-07-18
I don't know a lot about the technology but [here]("http://www.span.com/product_info.php?products_id=15709") and [here]("http://www.scan.co.uk/Index.aspx?NT=1-0-20-540-0") have them.

---

