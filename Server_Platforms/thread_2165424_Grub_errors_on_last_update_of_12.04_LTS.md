---
title: "Grub errors on last update of 12.04 LTS"
date: 2013-08-04
forum: Server Platforms
---

### Post by MakOwner on 2013-08-04
How bad is this?  I'm holding off on a reboot until I can get ensure a recoverable data backup and maybe figure out just how bad this is.
I'm accustomed to seeing grub errors during updates because I have an mdadm array made up of 2TB drives with gpt partitions but this string of errors is completely new.


```

Setting up apt-transport-https (0.8.16~exp12ubuntu10.12) ...
Setting up grub-common (1.99-21ubuntu3.10) ...
Setting up grub2-common (1.99-21ubuntu3.10) ...
Setting up grub-pc-bin (1.99-21ubuntu3.10) ...
Setting up grub-pc (1.99-21ubuntu3.10) ...
Installation finished. No error reported.
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found memtest86+ image: /boot/memtest86+.bin
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: sil: only 3/4 metadata areas found on /dev/sdk, electing...
ERROR: ddf1: both header signatures bad on /dev/sdr
ERROR: ddf1: both header signatures bad on /dev/sdb
done
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-51-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.2.0-48 linux-headers-3.2.0-48-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 67.6 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 124429 files and directories currently installed.)
Removing linux-headers-3.2.0-48-generic ...
Removing linux-headers-3.2.0-48 ...

```

---

