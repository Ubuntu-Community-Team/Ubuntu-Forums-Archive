---
title: "GRUB/Multiboot issue after migrating to SSD (can't boot correct Win7)"
date: 2015-01-03
forum: Windows
---

### Post by axelle_apvrille on 2015-01-03
Hello,

Santa Claus brought me a brand new SSD disk :) that I am trying to use. My host has 2 OS : a Linux and a Windows 7.

The root partition for Linux was on sdc1.
The system partition for Windows 7 was on sda1, and c: on sda2.
The new SSD disk is on sdb.

I have cloned the partitions I want to sdb (SSD disk), so that now I have:
[LIST]
[*]sdb1 should be identitical to sda1, ie that small Win7 boot partition 
[*]sdb2 should be identifical to sda2, ie my Win7 c: 
[*]sdb3 identical to sdc1, ie my linux root partition. 
[*]Grub2 is installed on /dev/sdc 
[/LIST]

Migration to SSD for Linux works: I successfully boot Linux with root partition being /dev/sdb3. Fantastic :) All fine on that side. 

Unfortunately, I can't get it to work for Windows : even though my GRUB sees the "new" Windows 7 on sdb, when I select that menu, I can verify that I boot on the "old" HDD (sda) and not sdb. 

--> What do I need to do to get GRUB boot the right Windows?

[Hint 1 (unsure) : my Windows partitions have the same UUIDs on sda and on sdb. Is that an issue? In another attempt, Imodified the UUID of the superblock, but that didn't seem to help. So, this is perhaps a bad lead.]

My boot info [http://paste2.org/z0tU4LG4](http://paste2.org/z0tU4LG4)

Kind Regards

---

### Post by oldfred on 2015-01-03
Moved to Other OS since Windows issues.

Not sure with Windows, but with Linux you cannot have duplicate UUIDs. I would change UUIDs on old install if you have good image backup also.

It looks like your partition size changed. NTF has to have in its partition boot sector the same size info as the partition table. A Windows chkdsk from your Windows or Windows repairCD/flash drive will fix that. 

I might disconnect sda, install a Windows boot loader into the SSD and see if repairs will let you get it working without conflict with old version. Windows does not like to be moved.
Grub will only boot a Working Windows so you need to resolve that first.

---

### Post by axelle_apvrille on 2015-01-03
I solved the issue this way:
looks like Win7 does not like not be on the first disk. So, I re-installed Win7 on the SSD, setting the SSD as first disk (dev/sda).
Then, I booted back to Linux and updated grub.

I wonder however what was the correct way to do this - without re-installing Windows. Looks to me like either a GRUB or a Windows boot issue.

---

