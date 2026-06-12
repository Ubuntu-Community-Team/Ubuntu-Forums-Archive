---
title: "I want to fall in Love with Ubuntu Servrer, but I can't"
date: 2011-05-30
forum: Server Platforms
---

### Post by Textstar on 2011-05-30
I have studied and learned a lot about the Server Edition of Ubuntu but I always have a problem of some kind. My latest one is with the fact that I use a lot of USB external hard drives which I tell Samba about and carefully mount. I can't understand why I have to remount the drives every time I reboot the server. All of the drives are listed in the fstab file so Ubuntu knows about them and  where they are. Am I missing something or is this the way it is supposed to be. Is there some way to permanently mount them where they are automatically recognized whenever I reboot.

---

### Post by ruffEdgz on 2011-05-30
If you can display the fstab for use, we can try and help you out on this.
```

cat /etc/fstab

```
Also, if you could attach your dmesg output to a file and place it on this post as well to see how your system is booting up.

Thanks!

---

### Post by hawkmage on 2011-05-30
If the USB drive is available at boot then they should be mounted.  Can you post your /etc/fstab and the output of the command "sudo blkid"

---

### Post by tgalati4 on 2011-05-30
I think the behavior is normal and a carryover from the desktop environment.  When a USB drive is plugged in, it shows up on the desktop, but is not mounted until you click on it.  There is no desktop in a typical server install, so I'm not sure how the USB drive is handled, but I'm guessing the kernel HAL or Hotplug or device handler picks it up and enumerates it (sudo fdisk -l), but it's not available to the file system until it's mounted.

I'm sure there's a script for the device handler that can be modified to automount USB drives.

---

### Post by hawkmage on 2011-05-30
> **tgalati4 said:**
> I think the behavior is normal and a carryover from the desktop environment.  When a USB drive is plugged in, it shows up on the desktop, but is not mounted until you click on it.  There is no desktop in a typical server install, so I'm not sure how the USB drive is handled, but I'm guessing the kernel HAL or Hotplug or device handler picks it up and enumerates it (sudo fdisk -l), but it's not available to the file system until it's mounted.

I'm sure there's a script for the device handler that can be modified to automount USB drives.
The difference in this case the OP mentioned that the USB drives have been added to the /etc/fstab so if the entries are correct the drives should be mounted on boot.

---

### Post by JPorter on 2011-05-31
It will be interesting to see the fstab config in this case.

Are you mounting in fstab by the device entry, or by UUID?


If it's a case where the USB drives aren't available yet when fstab does its initial mount, you could create a script to run mount -a to try to remount them as a last startup task.  It would be pretty unusual to have to do that, though.

---

### Post by JPorter on 2011-05-31
In fact, now that I think about it... what happens when you run
```
sudo mount -a
```from the terminal? Do your USB drives mount properly?  If not, you've got something wrong in your fstab file or you may need to disable USB automount entirely.

---

### Post by collisionystm on 2011-06-02
> **Textstar said:**
> I have studied and learned a lot about the Server Edition of Ubuntu but I always have a problem of some kind. My latest one is with the fact that I use a lot of USB external hard drives which I tell Samba about and carefully mount. I can't understand why I have to remount the drives every time I reboot the server. All of the drives are listed in the fstab file so Ubuntu knows about them and  where they are. Am I missing something or is this the way it is supposed to be. Is there some way to permanently mount them where they are automatically recognized whenever I reboot.


easy fix....

install usbmount

I have a desktop running 10.10 server. Had the same problem. Installed usbmount.

It mounts the drives under, /media/usb*

In my case, I have one drive, so its always /media/usb0

it works great. survives reboots. Dont over complicate things!

---

### Post by mnknight on 2011-06-04
for external drives you must use the UUID in fstab.conf! the server will get them all confused.

goto this link to understand more about using UUID.

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

hope this helps.

---

### Post by arrrghhh on 2011-06-04
> **mnknight said:**
> for external drives you must use the UUID in fstab.conf! the server will get them all confused.

goto this link to understand more about using UUID.

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

hope this helps.

+1, mount the drives by UUID.  Their /dev/ locations can change, their UUID will not.

---

### Post by Vaxon on 2011-06-16
```
sudo apt-get install usbmount
```

Automatically mounts usb drives on startup

---

