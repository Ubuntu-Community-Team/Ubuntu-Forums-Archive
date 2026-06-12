---
title: "command line help!"
date: 2010-05-12
forum: Server Platforms
---

### Post by AresArtemis1 on 2010-05-12
hi, professionals, I want to copy file from the Server cd drive and USB drive to the server root directory, but I haven't find any command of listing the cd drive or usb drive

many thanks,:guitar::guitar:

---

### Post by CharlesA on 2010-05-12
Why do you need to copy something to the root directory of the server? Just copy it to your home directory.

```
cp /path/to/file ~/
```

You will probably need to mount the cd/usb before you can access files on it.

```
mount /dev/cdrom /mountpoint/
```

---

### Post by windependence on 2010-05-12
I think he wants to know the device name of the USB or CDROM drive. 

To the OP, you can try doing a dmesg and look at what was detected on boot. You can also just do a df -h and you should see the device there if it is mounted. Alternatively, you can try fdisk -l to list all the devices.

-Tim

---

### Post by AresArtemis1 on 2010-05-12
> **CharlesA said:**
> Why do you need to copy something to the root directory of the server? Just copy it to your home directory.

```
cp /path/to/file ~/
```You will probably need to mount the cd/usb before you can access files on it.

```
mount /dev/cdrom /mountpoint/
```

hi, could you teach me how to mount USB drive, my IBM pc have 4 usb port, do I have to mount them one by one, or the Server has already set up them automatically, and could you tell me which command I can list all drives, which has been recongnized by Server,

best regards,

---

### Post by windependence on 2010-05-12
To see a list of your USB devices (the vendor and  device ID's), run: 
```
lsusb
```
To see all attached storage devices and their  partitions, run: 
```
sudo fdisk -l
```
To see information about currently mounted systems,  simply run: 
```
mount
```

-Tim

---

