---
title: "Can't read mounted EXT4 contents"
date: 2012-04-06
forum: Server Platforms
---

### Post by NightSky256 on 2012-04-06
Hi,
i've just setup an Ubuntu Server 11.10 over a preexistent OpenMediaVault (debian).
That distro was installed in a (dead) usb key, with the internal drive configured as storage.

I've booted with parted magic and resized the storage partition to have 20 free gigs at the begining. Installed UBUNTU then mounted my storage device on a mountpoint. (by putting uuid bla bla bla.. in fstab as always)

i can mount the drive with no errors, but i can't find any file in the mount point.

df tells me that the drive has used space.
i've also chowned and chmodded (755) the mountpoint (with the device mounted)...

no way...

any suggest ?

booting with partedmagic i can mount and read data from that partition, i can backup, format then restore... but if there is a faster way it would be really better !

---

### Post by darkod on 2012-04-06
Have you tried running fsck on the unmounted partition? Since the entry in /etc/fstab is mounting it at boot, unmount and try fsck. It might need it after the resize, especially if you never booted the old system after the resize.

---

