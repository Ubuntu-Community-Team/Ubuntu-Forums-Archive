---
title: "Newbie needs help migrating to larger hard drives in RAID 0 array."
date: 2007-02-16
forum: Server Platforms
---

### Post by bipolardave on 2007-02-16
--------------------------------------------------------------------------------

Hey there.

I recently picked up a Dell PowerEdge 2400 with onboard RAID controller and SCSI drives.

I installed Ubuntu server, GNOME, and even BOINC and the machine is running fine and currently crunching for SETI.

However, now it's time to put it to use as file and print server. Unfortunately, I installed Ubuntu onto a mirrored 9GB array. I now have several 18GB SCSI drives and would like to migrate the current setup from the 9GB drives to the 18GB.

Since there's very little on the machine now, I could easily reinstall everything in the course of an afternoon. But where's the challenge in that? What I really want to learn is how to migrate the exact disk image (partitions and all) to another, larger array. 

I've searched here and other forums but was unable to find anything specifically for this case.  Can anyone help in simple terms?

Thanks!

---

### Post by Quintin Riis on 2007-02-16
Basically, just copy the files, and install a bootloader.  Not much more than that.  Might need to edit menu.lst and fstab, but that's all.

---

### Post by bipolardave on 2007-02-17
> **Quintin Riis said:**
> Basically, just copy the files, and install a bootloader.  Not much more than that.  Might need to edit menu.lst and fstab, but that's all.

Thanks for the reply.

---

