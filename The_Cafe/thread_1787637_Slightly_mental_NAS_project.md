---
title: "Slightly mental NAS project"
date: 2011-06-21
forum: The Cafe
---

### Post by Grenage on 2011-06-21
I haze been toying with the idea of a new NAS, something that can hold around 10 drives.  Now there isn't much out there for the home market that fits the bill, so I'm considering making one.  Since I want it to be low power and simple, I was thinking about using something like a Beagleboard with a large SD.

SATA isn't an option for these kind of boards, so I was pondering the option of USB... for RAID.  The RAID should work, although I'm sot sure how such a system would handle 5 mirrors.  I normally run away from software RAID, but as this is a home machine and a bit of a mental project, why not.

I suppose the two questions I'm really asking are:

Has anyone had much experience with these sorts of boards?
What's mdadm like when using RAID1 or 10?  If the system catches fire, will the data be easily recoverable?

I anticipate some sort of fire.

---

### Post by Paqman on 2011-06-21
A dude from Canonical has been building a big cluster server out of Pandaboards with USB drives, you might want to check out his blog for tips:

[http://dmtechtalk.wordpress.com/](http://dmtechtalk.wordpress.com/)

---

### Post by Grenage on 2011-06-21
Great link, thanks for that.

---

### Post by tgalati4 on 2011-06-21
Low power, USB drives, green drives and large disk arrays don't mix well.  You can have enterprise-class drives in a SAN or server-grade disk enclosure and that will hold 10-12 drives.  For low power, you will run into all sorts of issues resulting in borked RAID arrays.  For JBOD (just a bunch of disks) a low-power, mini/micro/nano Intel or Via board with an extra SATA card or two will give you a better shot of handling such an array.

---

### Post by jerenept on 2011-06-21
> **Grenage said:**
> I haze been toying with the idea of a new NAS, something that can hold around 10 drives.  Now there isn't much out there for the home market that fits the bill, so I'm considering making one.  Since I want it to be low power and simple, I was thinking about using something like a Beagleboard with a large SD.

SATA isn't an option for these kind of boards, so I was pondering the option of USB... for RAID.  The RAID should work, although I'm sot sure how such a system would handle 5 mirrors.  I normally run away from software RAID, but as this is a home machine and a bit of a mental project, why not.

I suppose the two questions I'm really asking are:

Has anyone had much experience with these sorts of boards?
What's mdadm like when using RAID1 or 10?  If the system catches fire, will the data be easily recoverable?

I anticipate some sort of fire.

I have a knee-jerk FreeNAS reaction.
Also: please, for the love of all that is good, do not mix USB and internal drives in the same array. It will be slow.

---

### Post by Grenage on 2011-06-21
Thanks for the advice, chaps.  I know that a series of USB drives will be awfully slow, but with the drives being read-only 99.9% of the time, I figured it would be fast enough.

---

### Post by mips on 2011-06-22
Just get a low power atom board + additional sata controller(s) and be done with it. You are overcomplicating things and ending up with a inferior solution.

---

### Post by Grenage on 2011-06-22
While there's no doubt that the abilities will be inferior, I was after something that would have minimal power consumption.  Something like a panda board is only 4W under full load.

I have access to many old boards, so I might see how they fare.

---

### Post by BrokenKingpin on 2011-06-22
I like the general idea a lot... and could be a really fun project to work on. Keep us updated as you figure out the technical details.

---

### Post by Paqman on 2011-06-22
> **Grenage said:**
> While there's no doubt that the abilities will be inferior, I was after something that would have minimal power consumption.  Something like a panda board is only 4W under full load.

I have access to many old boards, so I might see how they fare.

The drives are likely to make up the bulk of your power usage. Your choice of main board/CPU will only be an overhead on top of that. You can get mini-ITX ATOM boards that run so cool they're fanless.

I have an ARM NAS running a RAID array and it is excellently low power, but i'm only running 4 SATA disks.

---

### Post by Grenage on 2011-06-22
I didn't realise how cheap and small the mini-ITX ATOM systems are now.  It'll come to less than a beagle/panda, and I can throw an SATA PCI-E Mini card in there.  I could also run the OS on USB flash.

I won't be able to get more than 4 SATA drives in there, but it's certainly an option.

---

### Post by mips on 2011-06-22
> **Grenage said:**
> 
I won't be able to get more than 4 SATA drives in there, but it's certainly an option.

Depending on the sata chipset used you can use a sata port multiplier to run up to 15 drives off a single sata port.

---

### Post by Grenage on 2011-06-22
> **mips said:**
> Depending on the sata chipset used you can use a sata port multiplier to run up to 15 drives off a single sata port.

I had no idea sata port multipliers existed, thank you!  That really seals the deal; as fun as the USB RAID ARM system sounds, this will be both cheaper and effective.

---

### Post by mips on 2011-06-22
> **Grenage said:**
> I had no idea sata port multipliers existed, thank you!  That really seals the deal; as fun as the USB RAID ARM system sounds, this will be both cheaper and effective.

Just verify the sata chipset used by the motherboard, this is VERY important as the port multipliers only work with a few of them!

Check this out [http://blog.backblaze.com/2009/09/01/petabytes-on-a-budget-how-to-build-cheap-cloud-storage/](http://blog.backblaze.com/2009/09/01/petabytes-on-a-budget-how-to-build-cheap-cloud-storage/)
They also use port multipliers.

---

### Post by Grenage on 2011-06-22
Thanks again. :)

I'll have a thorough read, and make sure that all the kit is compatible.  Now to design a chassis!

---

