---
title: "Loading data on to server"
date: 2010-12-12
forum: Server Platforms
---

### Post by peterthewolf on 2010-12-12
I have set up a headless NFS server and can write and read to it from my other pcs. I have a lot of data on an external usb hard drive. I would like to load this to the server via the usb connection. So with a keyboard and screen attached to the server I have followed many how tos on the net doing the advised mkdir and mount commands but to no avail. How can I do this.

---

### Post by papibe on 2010-12-13
I would start by making sure the USB disk is recognized, and have a device assigned. Compare the different outputs of the following commands before and after you connect the disk:

```
$ sudo lsusb
$ sudo fdisk -l
```

My guess is it would be linked to /dev/sdb1 or similar. In case there's no change in the commands above (disk not recognized), it may be possible to get it recognized by rebooting your machine with the disk connected and power on. In this case compare the output of the command before and after the reboot.

Regards.

---

