---
title: "Virtualbox correctly mounts some thumbdrive, but not WD passport"
date: 2010-05-08
forum: Virtualisation
---

### Post by bitter_mike on 2010-05-08
Hey all.

So I installed virtual box on a lucid host machine and created a Windows 7 guest. I can connect my various USB devices to the guest machine without a problem. My thumbdrive, which is formatted at fat32, is picked up by Windows 7 and mounts just fine and I can read and write to it. However, when I connect my 750GB WD passport, also formatted as fat32, the guest OS detects that it has been connected and if I go to devices, it lists an "External HDD", but it won't mount the filesystem and assign it a drive letter.

This drive works perfectly fine in Linux and when connected to "real" Windows 7 machines. I've also tried the karmic 3.1.6 release, the lucid 3.2.0 beta 1 and beta 2 releases. This problem is persistent in all of them. I've also tried disabling the USB 2.0 support but when I do that and connect the drive, it gives an error and says it can't install the mass storage device driver.

I've been poking around both the virtualbox and ubuntu forums and haven't really seen anything like this specific problem. Any ideas?

---

### Post by bitter_mike on 2010-05-08
Well no one answered, but I sorta figured it out.

So, here's what I did: I backed up the drive, deleted all the partitions, then created a single, 100GB FAT32 partition. This mounted on the Windows guest with no problems except a slight delay. I then deleted that partition and made a full 750GB FAT32 partition and tried to connect that. No dice. I then changed it to a 750GB NTFS partition and the guest had no problems with that.

My conclusions: virtualbox, for a reason I cannot explain, cannot handle very large FAT partitions. Maybe this will help someone in the future.

---

