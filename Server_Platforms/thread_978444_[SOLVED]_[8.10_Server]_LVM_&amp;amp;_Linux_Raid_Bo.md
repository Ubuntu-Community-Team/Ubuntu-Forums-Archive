---
title: "[SOLVED] [8.10 Server] LVM &amp;amp; Linux Raid Boot problem"
date: 2008-11-11
forum: Server Platforms
---

### Post by redwax on 2008-11-11
I have a software raid 5 (4 disks) containing an Volume Group split into swap/system/data.

Following a drive failure, I replaced the drive and started rebuilding, lovely!  Foolishly i needed to move the server (which had no sides on it) and nudged a cable (which was obviously flakey) and it disconneced another drive during rebuild.

The array was then inaccessable as 2 drives were effectively missing.  I re-added the 'nudged' one and it started to rebuild and then kept falling over until, nothing.  All I could get was an <initramfs> prompt.  It appeared that the superblocks had gone squiffy.  Being a noob, I figured I would see what the ubuntu installer saw on the disks. No array!  I then recreated (in the installer) the same array with the same disks and then it could see the VG.  I rebooted but after the grub loader it still says it can't find /dev/mapper/vg00-lv01--system.

I can actually manually mount this from a shell in recovery mode (on the install disk) and see all my lovely data, it just seems that the boot process falls over.

From <initramfs> at failed boot mdadm --detail /dev/md1 returns a message to the effect that there isn't an md1 (i'm not at the machine at the moment).  Assembkling the array at this point works and I can then mdadm --detail and see the array.

It occurs to me that they array isn't starting at boot, which probably has something to do with me 're-creating' it as outlined above.  Something to do with UUID maybe?  Like I said, I'm a semi-noob and don't understand the boot process in the situation sufficiently to resolve this problem so any help would be really appreciated.

Thank you

---

### Post by ikonia on 2008-11-11
first thing is booting off raid 5 is not a good call, it's not supported (people have used lilo and grub patches to make it supported - but it's not) you should have a /boot partition on a raid 1, or stand alone partition

(I'm sure plenty of people will argue about raid 0 or raid 5 /boot support - but bottom line is it doesn't work).

---

### Post by redwax on 2008-11-11
My bad,  I should have mentioned that the boot part is on a raid 1 array (md0) and that works fine (grub menu appears and then it says Starting... and after that stage it falls over

---

### Post by redwax on 2008-11-12
Bump...

To reconfirm:

/boot is on a raid 1 (md0)

vg00 is on raid 5 (md1) (consisting on 3 lv's, swap, system (/) and data)

Any help is greatfully apreciated!

---

### Post by redwax on 2008-11-12
I have managed to fix this!!!


I executed tune2fs -l /dev/md1 | grep UUID to find out the UUID of the array and got :

Bad magic number in super-block while trying to open /dev/md1
could not find valid filesystem superblock.

I stumbled upon this thread:

[http://ubuntuforums.org/showthread.php?t=883232]("http://ubuntuforums.org/showthread.php?t=883232")

using this

```
mdadm --create /dev/md1 --assume-clean --level=5 --raid-devices=4 /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2
```

All is now working again!

---

