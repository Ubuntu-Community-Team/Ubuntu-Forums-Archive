---
title: "VMware cannot drag and drop, cannot read flash drive"
date: 2008-08-18
forum: Virtualisation
---

### Post by Shippou on 2008-08-18
Hello folks...

To put it straightforward, how can you enable this? Drag and drop support is enabled in the options menu, and VMWare tools is installed. 

Also, my flash drive cannot be detected. It only detects the pseudo-hard drive it had created, as well as my DVD drive.

Please help.

---

### Post by fjgaude on 2008-08-18
Have you looked over this:

[http://ubuntuforums.org/showthread.php?t=791708](http://ubuntuforums.org/showthread.php?t=791708)

I think it tells all about vmware server and how to get the most from it.

---

### Post by Shippou on 2008-08-19
Followed the instructions, but still cannot detect flash drive nor drag and drop files. :(

Thanks for the help though.

---

### Post by fjgaude on 2008-08-19
Try this:

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Like so:

```
    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Then place in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Let us know how you are doing.

---

### Post by Shippou on 2008-08-19
Hello...

Sorry for the late reply...

Uhmm, where is the fstab file?

Thanks for the help.

---

### Post by fjgaude on 2008-08-19
The fstab file is in /etc, as /etc/fstab.

Place the line as the last one.

---

### Post by Shippou on 2008-08-20
Hello there...

I reinstalled vmware and followed the instructions. I still get the following error message when dragging and dropping files:
```

Unable to open: Virtual machine "/home/shippou/Desktop/Playlist.pls" is not in the inventory.

```

I haven't reinstalled XP, which is my guest OS.

Linux Mint is the host OS.

It can recognize my flash drive though. Thank you for the help. :)

---

### Post by fjgaude on 2008-08-21
You can only drag and drop files after you have setup Samba so that Ubuntu understands Windows files. Lots to learn here... go for it!

---

