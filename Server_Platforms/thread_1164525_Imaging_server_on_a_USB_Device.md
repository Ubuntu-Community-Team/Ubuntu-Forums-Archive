---
title: "Imaging server on a USB Device?"
date: 2009-05-19
forum: Server Platforms
---

### Post by mayhem1311 on 2009-05-19
At work we deliver computers to schools with their custom Windows XP image, all the hard drives are imaged at the warehouse but sometimes the image is corrupted or didn't work properly.

I'd really like to see if I could work out a mini imaging server on a USB device that the delivery guys could have on them that they could just boot up through the USB and image the hard drive  right on the spot.

The place I work isn't all thrilled about Linux and I'd like to open them up to the idea becase Linux is a really great OS.

---

### Post by windependence on 2009-05-19
Try to get very good at it before you push it there. If they think it's hard to use they won't like it even less. Yes, you could put the image on an 8 gig or larger thumb drive with Linux or better yet FreeBSD on it (it's smaller) and then just dd the image to the box using :

```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
```

There are several Linux and BSD distributions made specifically for this purpose.

-Tim

---

### Post by windependence on 2009-05-19
[http://featherlinux.berlios.de/usb-instructions.htm](http://featherlinux.berlios.de/usb-instructions.htm)

-Tim

---

