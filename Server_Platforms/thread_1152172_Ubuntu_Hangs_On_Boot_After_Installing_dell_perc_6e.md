---
title: "Ubuntu Hangs On Boot After Installing dell perc 6/e with Powervault MD1120 connected"
date: 2009-05-07
forum: Server Platforms
---

### Post by compmodder26 on 2009-05-07
We have a dell poweredge 2970 with a perc 5/i raid controller card that has local disks in a RAID 5 setup attached to it.  We are running out of storage capaicity so we purchased a perc 6/e raid controller and a powervault md1120 storage unit.  The md1120 has already been configured with a RAID 6 utilizing all 24 disks.  The perc 6/e card is recognized properly by Ubuntu.  The problem is when the powervault is connected to the perc 6/e and it is powered on.  When I boot Ubuntu, it starts to load just fine, then it halts saying "ata1: SATA Link Down".  It has this message 6 times with the ata1 changed to ata2, ata3, etc.  With the powervault turned off, Ubuntu boots just fine.

I'm sorry I can't give more detailed error messages.  This is on a production system and I can't bring it back down until later.

I've done some research and at first I thought it was an issue of Ubuntu assigning the wrong identifier to each Virtual Disk (/dev/sda, /dev/sdb), but the fstab is using UUIDs, so it should be able to overcome that.

I should also mention that the local RAID 5 is setup with an xfs filesystem and thus must use lilo for the bootloader.  I know lilo can't handle UUIDs and must rely on the older identifiers.  So perhaps this is my problem.  If so, can anyone tell me how to get Ubuntu to properly assign /dev/sda to the local RAID 5 array?

Any other thoughts on anything else that could be the problem?

BTW I have already talked with DELL and no luck there.

Thanks.

---

### Post by akShane on 2011-11-30
Did you ever get this figured out? I'm running into a very similar issue now.

---

### Post by compmodder26 on 2011-11-30
Yes I did.  It was lilo.  I just switched the partition identifiers in lilo.conf and it worked like a charm.

---

