---
title: "#!++ encrypted LVM do not work with btrfs"
date: 2018-01-11
forum: Ubuntu/Debian BASED
---

### Post by x3ua on 2018-01-11
Crunchbangplusplus fresh install works fine if choose encrypted LVM and let filesystem be EXT4. But if I change EXT4 to BTRFS, I got error:

```
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/debian--vg-root does not exist. Dropping to a shell!
```
The it drops to initramfs.
I've chrooted disks and checked everything, lvm2, btrfs-tools, cryptsetup.. everything seems to be ok.
I think btrfs support is missing from kernel.

Do you have any help how to solve this?

---

### Post by x3ua on 2018-01-12
I tried to add line dm-crypt ro /etc/initramfs-tools/modules
```
# sudo update-initramfs -u       
update-initramfs: Generating /boot/initrd.img-4.9.0-5-amd64
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-6ad51550-5b28-3fc1-4b-6c-2c14c560c19 - 
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-6ad51550-5b28-3fc1-4b-6c-2c14c560c19 - 
```

/dev/disk/by-uuid contains 6ad51550-5b28-3fc1-4b-6c-2c14c560c19

---

### Post by x3ua on 2018-01-12
Standard Debian Stretch install works fine with encrypted LVM and BTRFS. Something is missing from #!++ installation media, but my Linux skills are not good enough to solve this.

Building Openbox WM yourself with standard Debian install is too complicated, so it's a pity that this do not work. :/

---

