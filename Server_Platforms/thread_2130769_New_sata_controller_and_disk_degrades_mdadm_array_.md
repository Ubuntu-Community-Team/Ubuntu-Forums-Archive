---
title: "New sata controller and disk degrades mdadm array on boot"
date: 2013-03-30
forum: Server Platforms
---

### Post by epatch0321 on 2013-03-30
Was working:
Mobo has 4x sata controllers
/ booting from sata controller 1
/home on a mdadm raid 5 array booting from sata controllers 2 - 4 and drives sdb sdc sdd

Turned off the server, added a pcix sata controller with two sata ports on it and added one disk drive to it.

Power on the server, raid array boots degraded.

If I remove the sata cable from the new sata drive, still leaving new sata controller plugged in, the server will boot just fine; no degraded raid array.

I'm not sure what is going on here, thinking that maybe the new controller is hijacking the sdb sdc or sdd slot maybe?

Any help appreciated.

Linux 3.2.0-32-generic
Ubuntu 12.04

Eric

---

### Post by darkod on 2013-03-30
Why don't you confirm the device name of the new disk when it is plugged in?
sudo parted -l

Although, mdadm should work by UUID so even if one of the raid5 members changes the name, it should still assemble fine. Unless the ARRAY definition in mdadm.conf is by name, not by UUID. You can check the ARRAY definition and after that check all UUIDs with:
sudo blkid

---

### Post by epatch0321 on 2013-03-30
When I have the new disk plugged in it's putting me into some initramfs which wont let me do much.

Can't run parted -l 

blkid did run
 and it is showing the type of the new disk as linux_raid_member which is odd considering I haven't done anything to it yet.

I seem to remember trying to use it before and putting it to the side.  I'll try to wipe the disk and see if that helps.

Thanks for the suggestions!

---

### Post by darkod on 2013-03-30
If you have used it in raid before, you need to zero the superblock before you add it to the system again. It remembers the superblock info.

Just make sure you use the correct disk/partition, otherwise you might zero the superblock of one of the other raid members. Are you using the disk, like /dev/sde or the partition, like /dev/sde1?

If sde is the correct disk, zeroing the superblock would be like from live mode:
```
sudo mdadm --zero-superblock /dev/sde1
```

Never add disks you have used in mdadm before to the system without removing the superblock info.

---

### Post by epatch0321 on 2013-03-30
That was a previous attempt at building the array. The current array is a newly created array that did not include that disk.

Thanks or that information on the superblock though, I was not aware of it. I'm still learning :-)

Wiping the drive seems to have worked, I can now at least boot without going into a degraded array.

Moving on to growing the array now.

---

### Post by epatch0321 on 2013-03-30
Now I've got this issue:

running
sudo mdadm -add /dev/md0 /dev/sde1

gives me this
mdadm: option -d not valid in manage mode

I even tried logging in as root, since /home is mounted on md0, and unmounting /dev/md0 then running the above command. Same result.

---

### Post by epatch0321 on 2013-03-30
Bah! article I'm following had syntax incorrect.

it should be sudo mdadm --add /dev/md0 /dev/sde1

it's working now

---

### Post by darkod on 2013-03-30
Did you run the command as you wrote it, or you made a typo posting it? It should be:
```
sudo mdadm --add /dev/md0 /dev/sde1
```

The option is --add, not -add.

---

### Post by darkod on 2013-03-30
OK, you are aware that you need to run --grow after the sync is finished, right? Adding sde1 won't grow your array right away, if that's what you want to do.

Wait md0 to sync completely, and then you need to use like:
```
sudo mdadm --grow /dev/md0 --raid-devices=4
```

To grow it from 3 to 4 members.

After that you need to unmount /dev/md0 and expand the filesystem.

---

### Post by epatch0321 on 2013-03-30
Yep!

It's working on growing now. Looks like it is going to take a while based on  "watch cat /proc/mdstat"

tried using
echo 50000 > /proc/sys/dev/raid/speed_limit_min
echo 200000 > /proc/sys/dev/raid/speed_limit_max
to speed it up, still going to take a while.

one article says use:
e2fsck -f /dev/md0

another says use:
fsck.ext4 -f /dev/md0

both say to use:
resize2fs /dev/md0

to actually expand the filesystem though
Thanks for your assistance!!!

---

