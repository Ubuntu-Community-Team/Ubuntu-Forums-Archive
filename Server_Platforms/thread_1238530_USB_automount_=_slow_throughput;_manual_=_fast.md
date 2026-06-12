---
title: "USB automount = slow throughput; manual = fast"
date: 2009-08-12
forum: Server Platforms
---

### Post by jcornwall on 2009-08-12
While testing a new Seagate FreeAgent Go 320GB USB 2.0 drive with Ubuntu 9.04 AMD64 Server I observed the following:

[LIST]
[*]With 'usbmount' installed, plug drive in and let it automount. 'dd' write performance to /media/usb0/testfile is barely above 1.1MB/s.
[*]Unmount /media/usb0 and remount to /media/usb0 by hand. Write throughput rises to 30MB/s.
[/LIST]
The drive is correctly detected as 'hi-speed' upon connection. What might cause this?

---

### Post by jcornwall on 2009-08-13
I've solved this.

The usbmount package defaults to mounting USB drives with the safe 'sync' option to minimise data loss should the USB cable be pulled out. By switching this option off in /etc/usbmount/usbmount.conf my drive's throughput is much, much better.

Since I always umount before unplugging a USB drive this seems to be a better option for me. Very confusing one to hunt down.

---

