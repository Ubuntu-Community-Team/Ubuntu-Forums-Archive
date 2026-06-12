---
title: "Unmounting /var partition I get 'device is busy'"
date: 2011-03-18
forum: Server Platforms
---

### Post by shad0wca7 on 2011-03-18
I'm running my server from a usb key and I moved /var to another key in order to save some space and improve speed (helped a lot).

The problem I'm having though is that when shutting down / restarting I get:

umount2: Device or resource busy

Whilst trying to umount /var (formatted ext2)

I followed the tutorials on here to move /var although I did it this way:

Stopped all services / daemons (init 1) then copied the contents to the usb key, edited fstab, moved the original /var (then created the new 'blank' one with run and lock directories). Then rebooted... All works fine

If I do a 'shutdown now' and go back to the root console, sometimes I can see that rsyslogd and bizarrely mythtv-backend have restarted themselves (I can see that sometimes in the shutdown text output)... Why would they do that?

Upsettingly, even if I stop them and check /var is not being used (with lsof ) it still fails to umount?

Any advice?

---

### Post by shad0wca7 on 2011-03-19
I've been playing a bit more and still can't get a clean shutdown.. Here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# Volume_1 
UUID=b4d00614-57b4-4a74-a89a-f1d06debf75b	/mnt/sda2	ext2	defaults	1	1

# Volume_2
UUID=fd993fde-6098-4b7a-bd8d-5db38a690efb	/mnt/sdb2	ext2	defaults	1	2

# tmpfs to stop USB wear
tmpfs /tmp tmpfs rw 0 0

# /var on usb stick to save some space etc
UUID=08c7d078-5630-4a06-8da1-f5d8f00381b1  /var		ext2	noatime,errors=remount-ro 0 	1

# / was on /dev/sdd1 during installation
UUID=1a01ebd5-298a-4472-b9f4-914c11b4d7cf /               ext4    noatime,errors=remount-ro 0       1

# swap was on /dev/sdd5 during installation
UUID=ffef48ae-a495-40c7-b858-1107a2d48599 none            swap    sw              0       0

```

---

### Post by shad0wca7 on 2011-03-25
Bump?

Mods - is this in the best forum for this question?

---

