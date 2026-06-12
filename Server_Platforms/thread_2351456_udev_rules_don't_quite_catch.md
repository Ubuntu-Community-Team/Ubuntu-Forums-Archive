---
title: "udev rules don't quite catch?"
date: 2017-02-03
forum: Server Platforms
---

### Post by accentaigu on 2017-02-03
Dear forum,
in order to get consistent naming of my disks between reboots, I have set up some udev rules. After a reboot, it looks like this:
```
ls -l /dev/disk*
lrwxrwxrwx 1 root root   4 feb  2 19:24 /dev/disk1:1 -> sda1
lrwxrwxrwx 1 root root   4 feb  2 19:24 /dev/disk1:2 -> sdb1
lrwxrwxrwx 1 root root   4 feb  2 19:24 /dev/disk1:3 -> sdc1
lrwxrwxrwx 1 root root   4 feb  2 19:24 /dev/disk1:4 -> sdd7

```

After reapplying the rules, it looks like it should:
```
sudo udevadm control --reload-rules && sudo service udev restart && sudo udevadm trigger

ls -l /dev/disk*
lrwxrwxrwx 1 root root   3 feb  2 19:25 /dev/disk1:1 -> sda
lrwxrwxrwx 1 root root   3 feb  2 19:25 /dev/disk1:2 -> sdb
lrwxrwxrwx 1 root root   3 feb  2 19:25 /dev/disk1:3 -> sdc
lrwxrwxrwx 1 root root   3 feb  2 19:25 /dev/disk1:4 -> sdd

```

Does anyone understand why it does not catch on a reboot alone or what I should do about it?

Thanks,
Hägar

---

### Post by cariboo on 2017-02-03
Wouldn't it be way easier to mount your partitions by UUID eg:

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=25d3ae45-16ad-4792-b3bd-01c8c0379acc /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=EAE1-3E17  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdb3 during installation
UUID=ab973291-2bbb-4fa8-989a-207ec3f74f94 /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=e473f576-c5af-4410-ac9e-2e437325ceef none            swap    sw 
```

to find the UUID of each padtition use:

```
sudo blkid
```
the result should look something like this:

```
sudo blkid
/dev/sda1: UUID="25d3ae45-16ad-4792-b3bd-01c8c0379acc" TYPE="ext4" PARTUUID="203f88ff-3da1-49e8-b113-221180fe7a99"
/dev/sda2: UUID="EAE1-3E17" TYPE="vfat" PARTUUID="6a126cdf-dbef-43be-b38e-ea17593f406b"
/dev/sda3: UUID="0d1aa0d0-64b9-4b04-9587-c5f16cddaecd" TYPE="ext4" PARTUUID="b94deb92-7447-4a1f-8bb9-af7c56a7aec3"
/dev/sdb1: UUID="fa38bd0e-7846-4854-8182-53406d38db72" TYPE="ext4" PARTUUID="60a2dcef-174d-46a3-b9eb-87d0ae5550c1"
/dev/sdb2: UUID="e473f576-c5af-4410-ac9e-2e437325ceef" TYPE="swap" PARTUUID="3bf6ab9a-716c-494c-aa2e-20c82e9df6b2"
/dev/sdb3: UUID="ab973291-2bbb-4fa8-989a-207ec3f74f94" TYPE="ext4" PARTUUID="ea6fbf80-26c7-467f-8461-6abe1dedb547"
/dev/sdb4: UUID="0156abdb-30b2-4ba6-9448-b8a343f6bb38" TYPE="ext4" PARTUUID="681a0fec-692d-47a1-a420-c3b03bd29d8c"
```

---

### Post by accentaigu on 2017-02-04
Maybe, but the intention here is to be able to locate the physical location of a drive. disk1:4 being the first row, fourth drive. If a drive is replaced, the UUID is also changed, but the location (and thus the function) is the same.

/Hägar

---

### Post by accentaigu on 2017-02-07
Does anyone understand why the udev rules are not applied on a reboot?

Thanks,
/Hägar

---

