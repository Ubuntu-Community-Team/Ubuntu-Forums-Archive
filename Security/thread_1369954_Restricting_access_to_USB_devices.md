---
title: "Restricting access to USB devices"
date: 2010-01-01
forum: Security
---

### Post by dpcowx on 2010-01-01
Is it possible to allow the use of an external USB mouse and keyboard, but prevent the use of any other type of USB device?

I want to allow users of a shared/common computer to be able to plugin and use their own keyboard and mouse, but I don't want them to be able to plugin a digital camera, USB thumb drive, etc as this would allow them to read and view data off of this device; which is something I don't want this computer to be used for.

Is this possible?

Thanks,
Daniel

---

### Post by bruno9779 on 2010-01-01
you could allow only root to execute the command mount and umount:

```
sudo chmod go-x /bin/mount
sudo chmod go-x /bin/umount
```

This should work.

If it doesn't you'll need to edit your fstab, and put the noauto flag next to every usb FS.

---

### Post by falconindy on 2010-01-01
> **bruno9779 said:**
> you could allow only root to execute the command mount and umount:

```
sudo chmod go-x /bin/mount
sudo chmod go-x /bin/umount
```

This should work.

If it doesn't you'll need to edit your fstab, and put the noauto flag next to every usb FS.
BAD idea to mess with permissions -- especially things in /sbin. Also, mount only deals with disks and wouldn't prevent other kinds of devices like mp3 players, scanners, cameras.

You'll want to look into hotplug rules via HAL and DeviceKit.

---

### Post by BkkBonanza on 2010-01-07
I worked this out for another thread using udev.
See last post here,

[http://ubuntuforums.org/showthread.php?t=1355737&highlight=usb+read](http://ubuntuforums.org/showthread.php?t=1355737&highlight=usb+read)

---

