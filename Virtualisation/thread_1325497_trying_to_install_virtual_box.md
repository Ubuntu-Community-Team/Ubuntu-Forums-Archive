---
title: "trying to install virtual box"
date: 2009-11-13
forum: Virtualisation
---

### Post by ant2ne on 2009-11-13
```
ant2ne@2ne-buntu:~$ sudo apt-get install -y virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
ant2ne@2ne-buntu:~$ virtualbox
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.
Qt WARNING: QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
ant2ne@2ne-buntu:~$ 
e
```

```
ant2ne@2ne-buntu:~$ sudo apt-cache search virtualbox-ose-modules-generic
virtualbox-ose-modules-2.6.24-16-generic - virtualbox-ose module for linux-image-2.6.24-16-generic
virtualbox-ose-modules-2.6.24-18-generic - virtualbox-ose module for linux-image-2.6.24-18-generic
virtualbox-ose-modules-2.6.24-19-generic - virtualbox-ose module for linux-image-2.6.24-19-generic
virtualbox-ose-modules-2.6.24-20-generic - virtualbox-ose module for linux-image-2.6.24-20-generic
virtualbox-ose-modules-2.6.24-21-generic - virtualbox-ose module for linux-image-2.6.24-21-generic
virtualbox-ose-modules-2.6.24-23-generic - virtualbox-ose module for linux-image-2.6.24-23-generic
virtualbox-ose-modules-2.6.24-24-generic - virtualbox-ose module for linux-image-2.6.24-24-generic
virtualbox-ose-modules-generic - virtualbox-ose module for linux-image-generic
ant2ne@2ne-buntu:~$ uname -r
2.6.24-25-generic

```

---

### Post by ant2ne on 2009-11-13
I changed /boot/grub/menu.lst to exclude 2.6.24-25
```

# title          Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
# root           (hd0,1)
# kernel         /boot/vmlinuz-2.6.24-25-generic root=UUID=88e3db54-3656-41e2-9b$
# initrd         /boot/initrd.img-2.6.24-25-generic
# quiet

# title          Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
# root           (hd0,1)
# kernel         /boot/vmlinuz-2.6.24-25-generic root=UUID=88e3db54-3656-41e2-9b$
# initrd         /boot/initrd.img-2.6.24-25-generic

title           Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-24-generic root=UUID=88e3db54-3656-41e2-9b$
initrd          /boot/initrd.img-2.6.24-24-generic
quiet

title           Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-24-generic root=UUID=88e3db54-3656-41e2-9b$
initrd          /boot/initrd.img-2.6.24-24-generic


```
which forced me to use a 2.6.24-24. Suddenly virtualbox worked and vms were working. But it broke my nvidea


```
ant2ne@2ne-buntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 LE] (rev a1)
```

---

