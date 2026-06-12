---
title: "Creation of RAID-0 array in Disk Utility resulting in smaller than expected array?"
date: 2010-09-27
forum: Server Platforms
---

### Post by htnprm on 2010-09-27
Hello everyone. Apologies if this has already been asked. A search didn't find exactly what I was looking for. A little context:

I have a NETGEAR ReadyNAS NV+ with four 1TB drives in a RAID-5 array. This is our primary file storage. This has previously been backed up to a hardware RAID-0 array directly attached to our Windows server. The capacity of this backup array is no longer sufficient. So the plan was, take a bunch of 200GB to 320GB drives (And a 750) I had kicking around, chuck them in a couple of old SCSI drive enclosures I have collecting dust, attach them via IDA/SATA-to-USB adaptors to a USB hub, attach that to the server, create a JBOD array spanning the disks, and back up the NAS to that. Performance is  not an issue as this is just to be used for backup, with the idea being as near to zero cost as possible (Spend so far = NZ$100’ish).

The first hurdle I struck was Windows not supporting Dynamic Disks on USB drives (Required to create a spanned volume). At first I resisted using another machine (i.e. a machine running Ubuntu) as I didn't want to dedicate a piece of hardware to backing up the NAS. I then decided it would be acceptable to do this via a VM, which is what I've done.

So I have 10.04 running under VMWare Server 2.0.2 under Windows Server 2008 R2. The disks are all presented to the VM. I wasn't sure if I was going to end up creating the array under LVM or something else, but I noticed Disk Utility has an option to create an array, so I tried that.

When I add two 250GB drives, the array size is 500GB. When I then add a 160GB drive, the array size drops to 480GB. Huh? If I keep adding disks (Regardless of order) the final array size comes out at 1.8 TB, as per the attached screenshot. Now with the following drives, I expected something more like:

160 + 250 + 250+ 750 + 250 +200 + 200 + 250 + 320 + 250 + 320 = 3.2TB

Am I missing something or making a false assumption somewhere?

Cheers and thanks in advance,
Peter

---

### Post by arrrghhh on 2010-09-27
I think RAID arrays need disks of the exact same size... That's why JBOD would've worked for you, but RAID0 does not.

---

### Post by htnprm on 2010-09-27
Heh. You're right. Silly me never quite noticed, but the array size is 11 times the size of the smallest drive. This is what I initially expected with RAID-0, but a colleague (Who really should have known better) said drive sizes weren't an issue so I just thought Linux might have been a bit fast and loose when creating a RAID-0 array.

So there you go. Thanks for that. A 1.8TB array is 11 x 160GB drives. Now back to figure out how to do this with JBOD.

---

### Post by arrrghhh on 2010-09-27
Hahaha, no problem.

JBOD is doable, but kinda dangerous... I'm no expert, but I thought if one disk fails the entire array fails.  I could be wrong.  There was a thread about other alternatives to that, there was several interesting ones and some quite scary ones as well.  I'll see if I can find the thread, kinda slammed with other crap ATM unfortunately.

---

### Post by rubylaser on 2010-09-28
JBOD wouldn't be any more dangerous than RAID0.  In either case if you lose a disk, your data is gone.  If you really want to do what you've mentioned, you need to use LVM to span the disks together.  If you like having that data at all, I'd really suggest using a mdadm RAID5 (with a spare available) or RAID6 array.  It will cost some money to buy a few more drives to get back to 3TB, but if you ever need to rely on that data, having it in an array is much more reliable.

---

