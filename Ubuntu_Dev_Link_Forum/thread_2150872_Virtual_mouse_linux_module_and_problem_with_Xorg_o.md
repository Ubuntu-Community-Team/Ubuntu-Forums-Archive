---
title: "Virtual mouse linux module and problem with Xorg on ubuntu 12.04"
date: 2013-06-02
forum: Ubuntu Dev Link Forum
---

### Post by jonkyl on 2013-06-02
I'm trying to run virtual mouse driver from book "Essential Linux Device Drivers" but when I load this module into kernel using insmod in /var/log/Xorg.0.log I see:

```
[   757.212] (II) config/udev: Adding input device  (/dev/input/event10)
[   757.212] (II) No identifier specified, ignoring this device.
```

How can I force Xorg to don't ignoring this device, or what I must add to kernel module code to specific identifier for this event?

Kernel module code: [http://elinuxdd.com/~elinuxdd/elinuxdd.docs/listings/listing07.2.html](http://elinuxdd.com/~elinuxdd/elinuxdd.docs/listings/listing07.2.html)

---

