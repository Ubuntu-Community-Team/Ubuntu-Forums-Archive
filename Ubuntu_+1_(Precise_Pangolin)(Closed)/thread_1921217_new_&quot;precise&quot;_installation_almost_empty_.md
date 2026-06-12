---
title: "new &quot;precise&quot; installation: almost empty /etc/fstab"
date: 2012-02-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by surfer on 2012-02-06
i just did a fresh installation of precise (alpha-2). for the paritioning i chose: "Guided - Use entire disk as encrypted LVM" (or sth along these lines). now i checked what the installer wrote to [FONT="Courier New"]/etc/crypttab[/FONT]. everything in there is just what i had expected; something like
```
sda5_crypt UUID=... none luks
```

but [FONT="Courier New"]/etc/fstab[/FONT] contains only
```
UUID=... /boot/ext2 defaults 0 2
```
and nothing about how [FONT="Courier New"]/dev/mapper/sda5_crypt[/FONT] (i.e. the volumes in there) are mounted to [FONT="Courier New"]/[/FONT] and [FONT="Courier New"]swap[/FONT].

any ideas in which config files the respective entries are?

and: i have a second disk in that machine that is encrypted with dm-crypt as well and has not been mounted automatically by the installer. is there a more clever way to have it mounted during the boot process that to add the necessary lines to [FONT="Courier New"]/etc/crypttab[/FONT] and [FONT="Courier New"]/etc/fstab[/FONT]?

---

### Post by oldos2er on 2012-02-06
Moved to Ubuntu +1 (Precise Pangolin).

---

### Post by surfer on 2012-02-21
bump.

---

### Post by Gregory Lee on 2012-02-21
Except for the last two lines, my fstab was this (I repartitioned and added the last two lines later):
```
# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ecd9cd6a-16f6-478f-bbdc-c9b8839ebaf5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cf71ccb9-24dd-42d7-b746-6d63029c71b7 none            swap    sw              0       0
/dev/sda6       /user           ext4    errors=remount-ro 0       1
/dev/sda7       /extra          ext4    errors=remount-ro 0       1

```

Now that I read over the first post of this thread, I think my post is not especially relevant.  Sorry.

---

### Post by surfer on 2012-02-21
but that's for a non-encrypted / ; the device is just /dev/sda1 (and not /dev/mapper/something as it should be for an dm-crypt encrypted device).

but thanks anyway!

---

### Post by jbicha on 2012-02-21
Full encryption is relatively rare for Ubuntu as it currently requires the alternate installation.

---

### Post by surfer on 2012-02-22
be that as it may. i **took** the alternate install cd, i **did** encrypt the partitions and my question remains.

---

### Post by dcstar on 2012-02-22
> **surfer said:**
> be that as it may. i **took** the alternate install cd, i **did** encrypt the partitions and my question remains.

Try the current Beta install image and see if it still occurs, if it does then make a bug report.

---

### Post by surfer on 2012-02-22
i'm not sure if it is a bug; the system works, the disc is encrypted, i just don't see the entries i'd have expected in the fstab.

oh, now i checked back (after upgrades) everything is the way i'd expect it to be; the [FONT="Courier New"]/dev/mapper/...[/FONT] entries are now in the fstab.

strange... but solved for me! thanks everyone.

---

### Post by cariboo on 2012-02-22
Just out of curiosity, what's the output of:

```
df -h
```

---

### Post by surfer on 2012-02-22
as expected; the /dev/mapper/... stuff (linux volume manager; dm-crypt) is listed.

oh, but now i remeber: i did a fresh install and defined the encrypted devices and the volume manager myself...

---

