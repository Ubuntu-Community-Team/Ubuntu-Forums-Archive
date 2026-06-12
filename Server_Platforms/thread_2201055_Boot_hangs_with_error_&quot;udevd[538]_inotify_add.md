---
title: "Boot hangs with error &quot;udevd[538] inotify_add_watch(...) failed: invalid argument"
date: 2014-01-22
forum: Server Platforms
---

### Post by mdk2 on 2014-01-22
Hi,

I'm currently faced with the following situation:

when rebooting a Ubuntu 12.04 LTS server after updating (it ran perfectly for a year or so, I updated it around two months ago and rebooted with no problems, now about two weeks ago I again did an apt-get update/upgrade), it hangs before I even get to the Grub menu-selection with the following message:

```
udevd[538] inotify_add_watch(6, /dev/dm-2, 10) failed: invalid argument
```

The server has 4 harddrives, of which 3 are organized into an LVM group (this was not done by me, so I have no details on how this was performed, if needed I can supply the output of vgdisplay, which looks fine to me) and the last one ist used to boot the system.

When booting from a Ubuntu 12.04 Live CD (where I btw also get the udev error, but it only stalls the boot process for about 10 seconds), I can mount all the partitions without problems by doing
```
mount /media/ubuntuserver /dev/mapper/ubuntuserver-root (contains the root partition)
mount /media/sda1 /dev/ubuntuserver/boot (contains the /boot directory)
```

fsck reports no errors whatsoever on any of these disks. 

In similar threads I read that the installation of "cryptsetup" fixes the udev error for some, so I tried to do a chroot:

```
Boot from Live CD

sudo bash

mount /media/ubuntuserver /dev/mapper/ubuntuserver-root
mount /media/sda1 /dev/ubuntuserver/boot

mount -o bind /proc /media/ubuntuserver/proc
mount -o bind /dev media/ubuntuserver/dev
mount -o bind /dev/pts /media/ubuntuserver/dev/pts
mount -o bind /sys /media/ubuntuserver/sys

chroot /media/ubuntuserver /bin/bash

swapon /dev/mapper/ubuntuserver-swap_1
```

But I'm unable to finish an apt-get upgrade (update works fine), since whenever the post-installation triggers are to be processed, the systems just hangs and does nothing, no errors, no nothing.
Cancelling this process with ctrl+c finally gets me to the part where initramfs-update is called, which also stalls. When chrooting to the system from a 2nd shell, I see the new initrd File in /boot with 0 Bytes.

Any hint on what I'm doing wrong? Any hint on what else I could try? I'm running out of ideas...

Thank you in advance and best regards
Manuel

---

### Post by mdk2 on 2014-01-24
Ok, after some additional fiddling I can offer one more bit of information:

when calling 

```
update-initramfs -u -v
```

it stalls at the line 

```
Building cpio /boot/initrd.img-2.6.32-24-server.new initramfs
```

/sda1 ist mounted to /boot, on a 2nd shell I see the created file with a size of 0 Bytes, and that's it.

Any ideas?

Best Regards
Manuel

---

### Post by tekkitan on 2014-09-17
Did you ever figure out the issue? I have a server that experienced this and I can't get it to boot.

---

