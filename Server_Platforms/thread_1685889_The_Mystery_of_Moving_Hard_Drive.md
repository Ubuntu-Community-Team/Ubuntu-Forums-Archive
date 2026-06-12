---
title: "The Mystery of Moving Hard Drive"
date: 2011-02-11
forum: Server Platforms
---

### Post by CGW on 2011-02-11
Hello all:
I've been running a Ubuntu server box for some time...currently at 10.10.  I have a 20.5gb IDE drive that the server boots from (/dev/sda1).  I also have a 250gb SATA drive that I serve files from (/dev/sdb1).

Here's my problem.  I powered down my server to move it just a few feet and when I rebooted I rec'd an error that it couldn't mount the sata drive.  I did the usual "df" and "fdisk -l" command to find out that the drive was still there but for some reason the two drives had switched.  The IDE drive was now /dev/sdb1 and the SATA drive was /dev/sda1.  Obviously, the fstab was attempting to mount the wrong drive.

I rebooted again and rec'd the same thing.  I power cycled the server and after a few times the drives moved back!  Reboot again, then they've switched again!  This goes on randomly now.  If I reboot or power down the server I can't be certain the drives will properly mount.  sometimes it's correct, sometimes it's not.

I checked the BIOS and nothing has changed.  I will note that other than rebooting the machine I had probably never completely powered off the machine before now.  Regardless, now it's happening randomly on even reboots.  

Now I'm forced by my OCD to randomly reboot the machine to see what happens ;)

Any clues as to what's happening?

---

### Post by Grenage on 2011-02-11
This is down to BIOS, at least in part.  The drives are listed in the order they are detected, and that can vary on some machine.

Usually the drives are 'hard' assigned by UUID (unique identifier) in /etc/fstab.  Could you post your fstab file here?

---

### Post by CGW on 2011-02-11
Here's the fstab when it's working:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/server-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c38aa75f-17e7-4f05-8b0e-e109db3991e6 /boot           ext2    defaults     $
/dev/mapper/server-swap_1 none            swap    sw              0       0
/dev/sdb1 /data ntfs defaults 0 0

```

---

### Post by iissmart on 2011-02-11
Try replacing that /dev/sdb1 entry with the UUID.

UUID was created so that you don't need to worry about /dev names.

---

### Post by CGW on 2011-02-11
> **iissmart said:**
> Try replacing that /dev/sdb1 entry with the UUID.

UUID was created so that you don't need to worry about /dev names.

I'm seeing the UUID for the sda1 (boot drive) but not the sdb1.  where could I find that info?

---

### Post by Grenage on 2011-02-11
You can change the /data mount so that it uses a UUID instead of /dev/sdb1.  From a CLI, type:

```
sudo blkid
```

This will give you the UUID codes for the partitions in the machine.  Use the code in the fstab config file, and you should be 'sitting pretty'.

For your info, the UUID of a partition changes if any changes are made to the partition (resizing, changing the type, et cetera).

---

### Post by CGW on 2011-02-11
> **Grenage said:**
> You can change the /data mount so that it uses a UUID instead of /dev/sdb1.  From a CLI, type:

```
sudo blkid
```

This will give you the UUID codes for the partitions in the machine.  Use the code in the fstab config file, and you should be 'sitting pretty'.

For your info, the UUID of a partition changes if any changes are made to the partition (resizing, changing the type, et cetera).

Awesome people...thank you!

Of course, it was doing it at random so I guess I'll wait and see.  But after a few reboots/poweroffs it seems to be working fine.

---

### Post by Grenage on 2011-02-11
Our pleasure; I hope it helps.

---

### Post by CGW on 2011-02-11
Well, I literally completely shutdown the server and powered it on 10 straight times and it seems to be working just fine.

I'll remember that for any drives I add in the future.

Thanks again!

---

