---
title: "Manually installing from a live distro by copying the system"
date: 2020-01-14
forum: Ubuntu/Debian BASED
---

### Post by p5music on 2020-01-14
Hello,
I have a Lenovo G50 notebook with Windows10 and bitlocker.
I also have an hard disk that is able to boot MXLinux on a different computer from usb, but it is not possible with this notebook.
This drive has different partitions. I would like to use it to install another distro.
In this moment I am using a KDENeon live distro. I tried to copy all the root of the live distro to the partition on the usb hard drive but it fails.

I know I could use the installer, but I would like to copy all the system and then change the grub file on the MX root.
How to achieve that?
Thanks in advance

---

### Post by SeijiSensei on 2020-01-14
Use the installer, choose manual to assign the drive's partitions to the various OSs, then tell grub where to write the boot record. It will overwrite whatever was there before.

You can't copy over the files from the ISO image because they are all .deb files that need to be installed with dpkg.

---

### Post by p5music on 2020-01-14
@SeijiSensei
I am not trying to copy the files from the ISO, but from the root of the current system, it is in memory I think.
I do not want to use the installer now.
If it is possible I would like to proceed as I asked for.
Thank you

---

### Post by howefield on 2020-01-20
Moved to the "*Ubuntu/Debian BASED*" forum.

---

