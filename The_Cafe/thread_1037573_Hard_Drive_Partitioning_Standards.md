---
title: "Hard Drive Partitioning Standards"
date: 2009-01-11
forum: The Cafe
---

### Post by -kg- on 2009-01-11
I recently read a thread in which the person asking the question was using a proprietary Boot Manager and Partitioner called [BootIt.]("http://www.terabyteunlimited.com/support-bootit-next-generation.htm")  Apparently, it keeps it's own proprietary MBR and Partition Tables, allowing the user to create over 200 Primary partitions on a single physical hard drive.  This has set me thinking, and I've come to the conclusion that the Industry's Hard Drive partitioning standards need to be re-written.

With today's very large hard drives...some 1 Terabyte and larger...and considering the computer power we have available today, my thought is that we could drop the need for the "4 Primary Partition" rule and the need for Extended and Logical partitions, which confuse so many people and are seemingly no longer necessary.  The company who created BootIt came up with a software solution to it; why can't the Industry as a whole?

I would be interest in hearing discussion on why this should/shouldn't and how it could/couldn't be done.  I remember it taking many years to overcome the 640K RAM barrier (though a few OSes did it early); perhaps it is time to overcome another "Industry Standard" barrier, making things simpler on the computer tech and user alike.

---

### Post by gletob on 2009-01-11
There are two things I've always wanted from partitioning: 

The ability to have more than one extended partition for organization E.G. Windows system and recovery in one extended partition and linux and your home folder in another

and the ability to wrap current partitions in an extended partition

---

### Post by -kg- on 2009-01-11
> **gletob said:**
> There are two things I've always wanted from partitioning: 

The ability to have more than one extended partition for organization E.G. Windows system and recovery in one extended partition and linux and your home folder in another

and the ability to wrap current partitions in an extended partition

Just curious, but why?  What would be the advantage of having multiple Extended partitions, and why would you want to wrap existing Primary partitions in one (making them Logical)?

What I guess I'm asking is, what advantage would there be in having each Operating System in it's own Extended partition?

<edit>This exact thing is what I'm talking about.  [This site,]("http://www.pcguide.com/ref/hdd/file/structPartitions-c.html") while it doesn't really answer *why* the original "4 Primary partition" rule was implemented, explains it rather well.

A partition is used to separate an OS from it's data files, or one OS from another.  There is no greater degree of separation afforded by enclosing an OS and it's data partitions in an Extended partition, nor to enclose two (or more) OSes in their own Extended partition.

Absolutely the only thing that an Extended partition is created for is to circumvent the 4 Primary partition limit.  Nothing else.  It provides the capability of creating a large number of partitions, called Logical partitions, on the same hard drive...the Extended partition taking up one of the 4 Primary partition spaces.

It can be very confusing to the experienced computer person as well as the newbie.  That's why I advocate a re-write of the partitioning standards to allow a more reasonable number of Primary partitions and to eliminate the Extended partition altogether.

If one could create, say, the 200 Primary partitions that one is able to create using the BootIt scheme, there would be no reason to create an Extended partition, eliminating the confusion so many have on the subject.

---

### Post by mips on 2009-01-12
To do this correctly without hacks they would have to,

1. Change the BIOS as we know it today, it's about time anyway.
2. Create a new MBR which will be bigger than the current ones.
3. Relook at code in the OS as they all have limits in dealing with the amount of partitions.

---

### Post by ipatt on 2009-01-12
> **mips said:**
> To do this correctly without hacks they would have to,

1. Change the BIOS as we know it today, it's about time anyway.
2. Create a new MBR which will be bigger than the current ones.
3. Relook at code in the OS as they all have limits in dealing with the amount of partitions.

 The folks a Terabyte Unlimited have done just that - their BootIT allows for up to 255 primary partitions. How? They define and install an Extended MBR (EMBR). Incidentally, BootIT does much more. It includes the capability to move and resize partitions, has a multiboot capability and can make and restore partition images. All this for about $30.

---

### Post by -kg- on 2009-01-12
> **ipatt said:**
> The folks a Terabyte Unlimited have done just that - their BootIT allows for up to 255 primary partitions. How? They define and install an Extended MBR (EMBR). Incidentally, BootIT does much more. It includes the capability to move and resize partitions, has a multiboot capability and can make and restore partition images. All this for about $30.

Yes, but the thing is, it is a proprietary software solution, kind of like the software solutions to accessing large hard drives in the day before computer BIOSes were set up with LBA.

This partitioning scheme should be an industry standard, which would require a restructuring of BIOSes and OSes; especially their MBRs and access to the new Partition Table structures.  Also affected would be partitioning tools, which would have to be re-written to handle and allow this type of hard drive hierarchy and architecture.

A rather large and daunting effort, but so was LBA and breaking the 640 K memory barrier.  With increasing hard drive sizes and the increase in multiple OS usage, it's another barrier whose breaking is becoming increasingly necessary, IMO.

---

