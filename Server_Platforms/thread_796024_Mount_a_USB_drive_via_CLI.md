---
title: "Mount a USB drive via CLI"
date: 2008-05-16
forum: Server Platforms
---

### Post by /usr/bin/hacked? on 2008-05-16
How do I mount a usb drive via the command line and access it (the access part is important too!)

---

### Post by EXCiD3 on 2008-05-16
Pretty simple, here is an example:  
```
sudo mkdir /media/USBSTICK
mount -t vfat /dev/sdb1 /media/USBSTICK
cd /media/USBSTICK
```Explanation: mkdir creates a directory for the drive to be mounted, mount sets the drive to be mounted in the directory and cd changes the current working directory to where you mounted it to so you can access it.

---

### Post by /usr/bin/hacked? on 2008-05-16
How do I find the name of the usb stick though (/dev/hdx)?

---

### Post by EXCiD3 on 2008-05-16
It will be in the /dev folder on your system, most likely it will be the /dev/sdX1 with the X being the last letter in the alphabet of the sdX's listed last letter since it was added most recently. Make sure you use /dev/sdX1 in order to mount the first partition of the usb drive (most will only have 1 anyways). If you use /dev/sdX it will try to mount the MBR which you cannot access the drive to write to if mounted like that.

---

### Post by Monicker on 2008-05-16
You can also use

```
sudo fdisk -l
```

Then it should be easy enough to distinguish, based on the size of the usb stick.

---

### Post by /usr/bin/hacked? on 2008-05-20
Awesome, thank you muchly!

---

### Post by chochem on 2008-05-24
Easier still, use a label and mount it with 
```
sudo mount -L [label] [mount point]
```

If you haven't labelled your drive, check this [article]("https://help.ubuntu.com/community/RenameUSBDrive") on the wiki.

---

### Post by samosamo on 2008-05-24
you might be interested in autofs package for this, mounts it automatically when you "cd /misc/usb" or however you set it up

---

