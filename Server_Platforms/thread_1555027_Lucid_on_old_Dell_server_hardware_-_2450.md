---
title: "Lucid on old Dell server hardware - 2450"
date: 2010-08-17
forum: Server Platforms
---

### Post by MakOwner on 2010-08-17
Solved, sort of.
Just in case anyone else is foolishly chasing down this path as I just did. 

PE2450 with the latest BIOS (A09) and using the onboard Adaptec SCSI controller -- will install successfully from the minimal CD (network install); however it will not boot from the installed OS.

Short version is that it can't find the root device by UUID.

Boot into rescue mode and change the root=UUIDblah-blah-blah in grub.cfg to root=/dev/sd(x)(n)  

Boots fine after that - so far.

---

### Post by arrrghhh on 2010-08-17
This may cause issues down the road, and you'll want to change that back to the UUID.  You can find it by doing ```
ls -lah /dev/disk/by-uuid
```

Not sure why the UUID wouldn't get mapped correctly - I've seen this happen before tho.  Perhaps related to the SCSI controller...

---

### Post by MakOwner on 2010-08-17
> **arrrghhh said:**
> This may cause issues down the road, and you'll want to change that back to the UUID.  You can find it by doing ```
ls -lah /dev/disk/by-uuid
```

Not sure why the UUID wouldn't get mapped correctly - I've seen this happen before tho.  Perhaps related to the SCSI controller...

I have hammered at this for several days and can't find anything that will allow it to boot from the UUID label.  The boot fails and drops you into a shell and from there you can run the blkid program and the UUID of the partition matches the value in the boot command line in /proc/cmdline.

I'll just have to keep an eye out for grub updates and correct the configuration if it's changed, I suppose.  

Not an ideal solution by far, but the best I have found.

---

### Post by arrrghhh on 2010-08-17
Hm.  If you do find something better, please post back.  It's almost certainly that SCSI card, but I have no clue why.

---

### Post by MakOwner on 2010-08-17
> **arrrghhh said:**
> Hm.  If you do find something better, please post back.  It's almost certainly that SCSI card, but I have no clue why.

Upgrading to hardware built in this century is my best guess :)
I'm working on a 2550 with a Perc3 controller now. Bet that will be fun too.

---

### Post by arrrghhh on 2010-08-17
> **MakOwner said:**
> Upgrading to hardware built in this century is my best guess :)
I'm working on a 2550 with a Perc3 controller now. Bet that will be fun too.

Ha, well that would probably be your best option... ;)

---

### Post by MakOwner on 2011-03-29
> **arrrghhh said:**
> Ha, well that would probably be your best option... ;)

Just to update this thread...

[http://ubuntuforums.org/showthread.php?p=10612966#post10612966](http://ubuntuforums.org/showthread.php?p=10612966#post10612966)

Same situation occurs on a PE 1750 after adding a new PCI-X SATA controller.
9.10 works, 10.04 works without the controller added, but adding in that controller breaks grub.  

Now a 1750 isn't the newest hardware out there, but it sure as hell isn't old enough to be trashed yet.

---

