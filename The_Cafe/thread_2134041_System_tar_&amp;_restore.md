---
title: "System tar &amp; restore"
date: 2013-04-10
forum: The Cafe
---

### Post by tritonas00 on 2013-04-10
Hi ! :)

We working on this project and we would like to share it.

System tar & restore contains two bash scripts, backup and restore.

The purpose is to make the process of backing up and restoring a full GNU/Linux installation easier using tar or transfer an existing installation using rsync.

Supported distributions: Arch, Debian, Fedora

-CLI and Dialog interfaces
-Easy backup and restore wizards
-Uses tar / bsdtar to create and restore backups
-Creates *tar.gz*, *tar.bz2* or *tar.xz* archives
-Uses rsync to transfer a running system
-Supports Grub2 and Syslinux

[Documentation](https://github.com/tritonas00/system-tar-and-restore/blob/master/README.md#about)
[Stable Releases](https://github.com/tritonas00/system-tar-and-restore/releases)
[Changelog](https://raw.github.com/tritonas00/system-tar-and-restore/master/changelog)
[Demo](https://www.youtube.com/watch?v=dr5ZB3ajhTQ&hd=1)

You can try it in your usb flash, a second disk or virtualbox.

Worked nicely with lubuntu and kubuntu :D

---

### Post by kevdog on 2013-04-10
Is there audio with this file?  I kind of confused.  I can hardly read what is on the screen.

---

### Post by tritonas00 on 2013-04-10
> **kevdog said:**
> Is there audio with this file?  I kind of confused.  I can hardly read what is on the screen.

Please change video quality to 720p.

Documentation is in the Git link.

---

### Post by kevdog on 2013-04-10
Ok I watched the video -- thanks for suggestions.  How does this compare to other backup options -- like rdiff-backup, duplicity, or rsnapshot?  I currently exploring obnam on arch and I think its pretty cool I haven't done any mission critical backups.

---

### Post by tritonas00 on 2013-04-10
Thanks for watching.

It uses tar to create and restore backups, or rsync to "on the fly" transfer the system.

Then it generates fstab, rebuilds initramfs for every available kernel, regenerates locales and installs a bootloader (grub2 or syslinux)

More info in the documentation :)

---

### Post by kevdog on 2013-04-10
Sounds like a great project and something I'm going to check out!!

---

### Post by tritonas00 on 2013-05-26
Updated to 3.1

Added raid support, log for restoring process, tar / rsync progress info and many other improvements.

Enjoy :)

---

