---
title: "Add RAID0 to my sistem"
date: 2009-01-19
forum: Server Platforms
---

### Post by xeo_pt on 2009-01-19
Hello,
I add two 512Gb to my system (a server without Desktop), and now I need to create a RAID0 (512 Gb + 512 Gb) to make a 1 Tb partition.
I know how to do it when installing the system from scratch, but I don't want to re-install the system.
How can I do from the command line?

Thank you in advance for your help.

---

### Post by fjgaude on 2009-01-19
If you are booting from other than these two big drives it is easy with a program called **mdadm**, from the respository if you don't already have it on your system:

```
sudo mdadm --create dev/md0 --level=0 --raid-devices=2 /dev/sd[ab][n]
```

Then install a filesystem:

```
mkfs -t ext3 /dev/md0
```

Make a mountpoint and put a line in your **fstab** file.

You might want to study the **man** pages for mdadm.

---

### Post by xeo_pt on 2009-01-23
> **fjgaude said:**
> If you are booting from other than these two big drives it is easy with a program called **mdadm**, from the respository if you don't already have it on your system:

```
sudo mdadm --create dev/md0 --level=0 --raid-devices=2 /dev/sd[ab][n]
```

Then install a filesystem:

```
mkfs -t ext3 /dev/md0
```

Make a mountpoint and put a line in your **fstab** file.

You might want to study the **man** pages for mdadm.
Thanks for your help.
But first I had to create a partition with fdisk of type fd, reboot, and make your procedures.

Thanks a lot.

---

### Post by fjgaude on 2009-01-23
Great, you are on your way!

---

