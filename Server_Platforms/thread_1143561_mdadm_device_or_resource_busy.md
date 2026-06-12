---
title: "mdadm: device or resource busy"
date: 2009-04-30
forum: Server Platforms
---

### Post by TheDauthi on 2009-04-30
After my recent upgrade to Jaunty, I had a problem.  A big problem.
My software raid [raid5, 4 discs] decided not to come up.  Looking at it - two drives degraded?  That's... not good.

After taking a look around, I see no error messages in dmesg, no log messages that indicate any problems.  I run smartctl (long test), and it comes back clean.  All four drives are fairly new.  mdadm -E shows everything looking... well, like two drives failed.  But, after a lot of searching, if I'm fairly sure that the drives themselves are unchanged, I should be able to re-create the raid array from the 4 drives and it'll work.

So I try to recreate the array
```

mdadm --create /dev/md2 --level=5 --raid-devices=4 /dev/sd[bcef]1 

```which gives me
```
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=100440512K  mtime=Tue Apr 28 18:52:55 2009
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Apr 30 00:00:01 2009
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Apr 30 00:00:01 2009
mdadm: Cannot open /dev/sdf1: Device or resource busy
mdadm: create aborted

```...
Some googling suggested that the it was possible the fakeraid modules were loaded, but I don't see them in lsmod.  Others suggested disabling swap - swapoff -a didn't do anything.
lsof |grep for /dev/sd[bcef] or /dev/sd[bcef]1 shows nothing
nor for /dev/md0 and /dev/md2

Now, for the weird thing, and what I don't understand:
It fails on different drives each time.
Each time, after a reboot, the drive it fails on is different!  For example, that was from my current reboot.  If I reboot again, it's very likely to be /dev/sdb1 that is unreadable.

I've also switched out cabling, assuming the problem might be that.

Any thoughts or suggestions?

---

### Post by fjgaude on 2009-04-30
Likely the old mdadm.conf file is no longer valid. Try this and re-boot:
```

sudo sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

If this doesn't work, let us know.

---

