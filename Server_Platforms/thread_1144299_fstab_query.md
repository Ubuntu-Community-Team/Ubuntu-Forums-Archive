---
title: "fstab query"
date: 2009-04-30
forum: Server Platforms
---

### Post by maclenin on 2009-04-30
With reference to my [_raid/lvm configuration_]("http://ubuntuforums.org/showpost.php?p=7134682&postcount=4"), I have 3 active/bootable partitions across 3 drives:

/dev/sda1*
/dev/sdb1*
/dev/sdc1*

2 of these partitions make up an unmounted /dev/md0 RAID1 array:

/dev/sda1*
/dev/sdb1*

NB1: I believe I still need to install grub on /dev/md0 (sda1 and sdb1).

The 3rd partition (non-raid and non-lvm) is currently mounted as /boot:

/dev/sdc1*

NB2: I am running one OS (Ibex)....

Question:

How might I enter BOTH /dev/md0 (as the "default") AND /dev/sdc1 (as the "fallback") into fstab so that they are BOTH available as bootable options to my system (via the grub menu at boot or as "fallback" options (in menu.lst) should something go wrong with the other drive)?

Thanks for the assistance!

---

### Post by maclenin on 2009-05-01
...additional thoughts....

1. Install grub on /dev/md0...

...grub> find /grub/stage1 reveals

```
(hd2,0)
```

...first to /dev/sda1
```
grub> root (hd2,0)
grub> setup (hd0)
```
...next to /dev/sdb1
```
grub> device (hd0) /dev/sdb1
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

2. Modify menu.lst to make /dev/md0 default and /dev/sdc1 the "fallback"....

2.a. Change groot to = (hd0,0)

Questions:

Does /dev/md0 need to be mounted in order for grub to be installed on its sda1 and sdb1 devices?

When adding /dev/md0 to menu.lst - do I create separate (UUID) entries for sda1 and sdb1 (the devices within the RAID array)? Or a just single UUID entry for /dev/md0?

Thanks, again, for any thoughts....

---

### Post by maclenin on 2009-05-03
Anyone?

---

