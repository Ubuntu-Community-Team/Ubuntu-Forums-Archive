---
title: "RAID 1 OS drive &quot;BOOT_DEGRADED=false&quot; not working?"
date: 2012-11-14
forum: Server Platforms
---

### Post by OneOfMany07 on 2012-11-14
I'm setting up a software RAIDed boot and root desktop install.  Originally I chose BOOT_DEGRADED=true during setup.  But after talking with people here we wanted to change that.  So I followed the instructions on [https://help.ubuntu.com/12.04/serverguide/advanced-installation.html]("https://help.ubuntu.com/12.04/serverguide/advanced-installation.html"), shutdown, disconnected one drive, and booted.  It booted just fine to the user selection screen.

mdadm against both /dev/md# entries show a degraded status, but I expected to be stopped at a recovery console.  I double checked the setting is in the file /etc/initramfs-tools/conf.d/mdadm as I'd used ```
sudo dpkg-reconfigure mdadm
``` to change the setting and I wasn't sure it was permanent.

Any suggestions?  Or is this not a valid setting on a mirrored drive?  If so it would be nice if it wasn't available to scare newb's like me ;)

---

### Post by darkod on 2012-11-14
This is just a wild shot, but sometimes after changing mdadm important settings, I've seen suggestions to run:
sudo update-initramfs

(if I remembered it correctly).

See if that helps to apply the setting not to boot degraded.

Also when disconnecting disks to make a test, make sure they are synced first.

For example, a sync after the first test might not have finished yet, and if you unplug a disk for a second test it might loose the connection with the other disk and get really messed up.

---

### Post by OneOfMany07 on 2012-11-14
I just found that my root space is marked degraded even with both drives up.  Maybe that is part of the problem too?

Off to search out repair instructions.

---

### Post by OneOfMany07 on 2012-11-15
Looks like I can't see the recovery console (black screen after disconnecting a drive after updating the initramfs and sync'ing the drives so they were clean).  Guessing it'll be better to make a new thread.

---

