---
title: "How do i remove a disk from an LVM?"
date: 2007-05-22
forum: Server Platforms
---

### Post by feenster on 2007-05-22
Hi all,
I've got a pair of 500GB SATA drives running in a RAID-1 array created using **mdadm**. I've then added them into an LVM group (as i planned to expand the storage). However, i'm now rebuilding the server, so need to take one of the disks out to copy the data off.

How do I remove the disk from the LVM, de-RAID it, and get it to a point where the data is available in full on both disks from the RAID-1 pair?

Cheers,
  Matt

---

### Post by craigp84 on 2007-05-23
Hi Matt,

Save yourself some grief. Just shut the box down and pull a power plug off one of the drives - no danger of reinstalling over both drives when you're configuring the RAID array again (you'll build a degraded raid array during install).

Sounds like you don't have much of a backup plan in place though, maybe that should be a higher priority than the reinstall?

HTH,

-c

---

### Post by feenster on 2007-05-23
Hi Craig,
I'm not sure if i made myself clear. What i want to do is remove a disk from the LVM (which is also a RAID1) and put it into another machine to copy the data off. I thought if i just pulled the disk out, the RAID would be damaged, and due the way the LVM was setup, i wouldn't be able to mount the disk and access the data anyway.

If that's not the case, can you tell me how to mount a volume that has come from the LVM and is part of a RAID-1 array?

Cheers
    Matt

---

### Post by craigp84 on 2007-05-23
> If that's not the case, can you tell me how to mount a volume that has come from the LVM and is part of a RAID-1 array?

Shutdown the host box it's currently in.

Pick a drive, any drive.

Connect it to your new linux box - the one you're copying too.

The md driver in the kernel will recognise the disk @ boot time, and bring it up as a degraded array (there's only 1 disk). The lvm stuff will kick in.

You can now mount the lvm volumes and copy.

This sounds pretty crazy way to do this though - what's wrong with sitting the boxes next to each other and running some cat 5 between them (assuming they're not already networked or you would have just ftp'd the stuff across)

-c

---

### Post by feenster on 2007-05-23
Hi,
The reason for not just copying it across the network is because there is about 600GB of data to copy! Having said that, i've started it going now. It's just reallllllllyyyyyyy slooooooowwwwww

---

### Post by Brazen on 2007-05-23
> **feenster said:**
> Hi,
The reason for not just copying it across the network is because there is about 600GB of data to copy! Having said that, i've started it going now. It's just reallllllllyyyyyyy slooooooowwwwww

It may be slow, but it's probably a safer solution.  All in all, pulling the drive should go off without a hitch as craigp84 said, but personally I would rather just start the network copy and then go do something else while it finishes.

---

### Post by craigp84 on 2007-05-23
Yeah, Brazen++

-c

---

### Post by feenster on 2007-05-23
Hi,
Thank you both for the advice. I have taken it onboard and started the data copying over the network. I may have to fill in some gaps tomorrow from a backup i have on an IDE hard drive, but hopefully the bulk should be out of the way :)

Matt

---

