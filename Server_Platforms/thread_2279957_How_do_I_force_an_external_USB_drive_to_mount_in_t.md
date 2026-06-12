---
title: "How do I force an external USB drive to mount in the same location on every reboot?"
date: 2015-05-26
forum: Server Platforms
---

### Post by noSelf on 2015-05-26
I have a older desktop machine that I use as a fileserver and backup host for my family's laptops and netbooks. It's running 8.04 LTS (yes, I'm planning an upgrade). I've sucessfully used commodity-priced external USB hard drives (I like the Western Digital portables) for for simple-but-effective rsync backups, with no problems. I export the disks via nfs as well as with samba (so my windows vms can reach the same files that the Ubuntu machines). I recently had to add a second external drive  for a second-level backup, and discovered that I can't rely on the disks automounting in the same /media/usbX location upon reboot. I'm a bit of a newbie in this area.

What's the preferred method for forcing a usb drive to mount in the same path after each reboot?

TIA!

---

### Post by darkod on 2015-05-27
First check the uuid values for each partition on the usb disks. It's a long string. You can check all uuid in the system with:
sudo blkid

Then open /etc/fstab as sudo for editing and make an entry with your mount point and filesystem type. Lets assume you have ext2 on the partitions:
```
UUID=<string>   /mountpoint   ext2   defaults   0   0
```

That will mount it each time at /mountpoint. Make sure you get the uuid right. You can make as many entries as you like. Save and close the file. You can remount without rebooting with:
sudo mount -a

---

