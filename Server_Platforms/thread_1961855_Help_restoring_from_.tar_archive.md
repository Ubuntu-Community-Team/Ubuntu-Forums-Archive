---
title: "Help restoring from .tar archive"
date: 2012-04-20
forum: Server Platforms
---

### Post by Drak3 on 2012-04-20
so, somehow i managed to mess up the installation of ubuntu 10.04 LTS i had.  long story short, I've reformatted my boot drive and I've discovered that despite having many backups, the fact that i've reformatted means the UUID of the current partition to be restored does not match the UUID of the backed up partition.

ive tried doing a fresh install, to generate the grub files specific to the new partitions UUID, and overwriting those onto the backup after restoring.  again, long story short, i've still yet to restore my OS.

ive also tried restoring and followling the guide [**here**]("https://help.ubuntu.com/community/BackupYourSystem/TAR") with regards to reformatting.  i.e., manually setting the correct UUIDs in /etc/fstab and /boot/grub/grub.cfg (not /boot/grub/grub.lst becuase of the info [**here**]("https://help.ubuntu.com/community/Grub2#Selected_Problems_and_Bugs")), and still nothing.

so, what I'm wondering is, does anyone know how I might go about restoring my OS, give my situation.  

this really seems like it should just be a matter of restoring most files from my backup while keeping certain files from a "fresh" install becuase of the reformat, but I'm really at a loss as to what thos are.  it also seems reasonable that i could restore certain parts of my backup onto a fresh install with similar effect.

any help anyone could provide would be AWESOME!

---

### Post by Drak3 on 2012-04-20
figured out my restore problem.  i had to restore grub.  after unpacking the tar archive if you restore grub, it booted for me.  though the problem that led to the restore is still there...

---

