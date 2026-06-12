---
title: "Scanner keeps moving around on me..."
date: 2012-03-17
forum: Server Platforms
---

### Post by fizgig on 2012-03-17
My scanner seems to decide to be found at a different location in the usb bus depending on what its mood is at computer reboot.

Now it is at: libusb:005:002
Before, it was at: libusb:006:003

And so on...

I have it attached to Ubuntu 10.04 headless server and I'm running the php scanner web portal which works great if I reconfigure it at every reboot to point at the new scanner location.

Anyone know how I can make this stable?

---

### Post by volkswagner on 2012-03-17
You may want to setup a udev rule for the scanner.

I have [this]("http://ubuntuforums.org/showthread.php?t=168221&highlight=udev+rules") book marked.  It is old, so I'm not sure what has changed or if it is still relevant.

---

### Post by fizgig on 2012-03-17
Appreciate the idea.  I did do something like this a long time ago for a usb harddrive and it worked.  Unfortunately, 10.04 doesn't appear to have udevinfo anymore and it appears to be necessary in that tutorial.

---

### Post by volkswagner on 2012-03-17
Perhaps you can get enough information from lsusb to create a rule.

```
lsusb -v
```

---

