---
title: "LVM on RAID or RAID on LVM?"
date: 2009-06-26
forum: Server Platforms
---

### Post by Luke has no name on 2009-06-26
My analysis leads me to believe that running all your disks on an LVM, then creating a RAID based on partitions in the LVM is more flexible.

Thoughts?

---

### Post by nixomose on 2009-08-04
I had this exact idea a few days ago.
I've found some messages in gentoo from 2004 saying it's possible and some from 2006 in ubuntuforums saying it's not.
I figure by now it's probably possible, and seems to me to make sense. Sure more people run lvm on raid, but there certainly is value in running raid mirrors over 2 identical lvms.

So... does anybody know how to do it?

---

### Post by finite9 on 2009-08-05
I used to run my disks on mdadm/LVM and then dmcrypt.  Three tiers.  What a pain in the *** to manage it was.

I discuessed it with one of the Unix techies at work and he said it wasn't worth the hassle.  For a disk array that doesn't do much else, always on etc home server, you probably dont get that many issues once its all up and running, but when your working with it day in day out and you see all the management issues that arise, it really puts you off.

If something goes tits up with lvm, then it's a mess to get it all working again.  same if mdadm freaks out and lvm is still intact.  It's simply harder to manage.

Now I just ran mdadm and plan my requirements better.  LVM is definitely best for a OS disk though as itäs easier to manage the partitions, but if you have a seperate big disk array for storing your media etc, then it's simpler to just raid it and have done with it.

---

### Post by fjgaude on 2009-08-05
And I would suggest before using mdadm to study just what it's all about and how to use it in all the situations you will face over the months, years that an array is active. As starters:

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)
[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)
[http://linux-raid.osdl.org/index.php/Growing](http://linux-raid.osdl.org/index.php/Growing)

What ever you do, have fun!

---

### Post by giggins on 2009-08-05
Depends on what you're looking for. When you say "more flexible", what do you mean? Surely LVM is more flexible for expanding a volume's size (especially since it can do it on-the-fly), but I see how using RAID on top of LVM is easier for only using RAID on what you want to be redundant.

---

### Post by windependence on 2009-08-06
I can't see any reason to put RAID volumes on top of LVM, in fact, I can think of a few reasons not to. 

If you don't need RAID, don't do it just because it's "cool". I see way too much of that here and it's just not necessary. LVM give you flexibility to expand and contract partitions and add and remove physical disks.

-Tim

---

### Post by DEFleener on 2010-04-20
I actually have a use-case for RAID on top of LVM. Maybe someone smarter than me can tell me how to do it differently?
 
I have multiple old hard drives lying around that I'd like to put to some use. They are of various makes, models, and sizes. It would seem that LVM could be used to make some logical volumes of all the same size, which could then be joined together in various ways by software RAID. In my case, I think RAID 10 would suit me best. The only reason I would use LVM is to get uniform volume sizes, because that is the best way to utilize all the available space in RAID.
 
I have some other old computer parts around that I could then use to build a file server for my house. Out of all the hdd's I have, I would probably put the smallest one(s) in my desktop computer(s), and the others in the file server. Then, I can use what I have, instead of constantly running out of room on my hard drive(s), while at the same time, having a half-dozen or more of them lying around, not being used.
 
Because of all these disks being at least seven or eight years old, or more, the redundancy of RAID would make it less dangerous to store my files on these things, while the flexibility of LVM would help me add more in the future without too much fuss. And when one of the physical disks fails, I could adjust the LV's and not have to replace the disk if I don't want to. I would just have less storage until I did.
 
I know LVM itself has striping, and if it had mirroring too, and could operate as a RAID on it's own LV's, that would be the best!

---

### Post by finite9 on 2010-04-21
I wouldn't recommend this.  f you have some 7yr old drives from the same period that have same spindle speed same interface type, then no, this would not be an issue, but to combine hard drives with different interfaces, if they are several years apart in age, for examlpe an ATA that supports DMA66 and one that doesn't support DMA at all or o much lower version will mean that the discs will perform differently, and in that case, it's not really a good idea to mix these drives in the same volume group.

---

### Post by DEFleener on 2010-04-21
You're probably right. I didn't think about different drive capabilities causing problems with LVM. I know the drives I have are all ATA133, but I'm not sure if the spindle speeds are all the same. I would expect most of them are 5400. As for other specs, I have no clue. I haven't really looked at them lately. I don't have enough PATA connections in my computer to do this anyway, but I thought it might be a cool thing to be possible, if the conditions were right.
 
Still, if someone did have several similar drives, other than the capacities being different, my theoretical use case would make RAID on top of LVM very useful. RAID won't use all the space you have unless the capacities are the same for each volume. LVM under a software RAID, just to even out the capacities, would be cool.

---

