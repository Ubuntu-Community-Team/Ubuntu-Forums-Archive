---
title: "grub fail after dist-upgrade"
date: 2010-11-10
forum: Server Platforms
---

### Post by enboig on 2010-11-10
After upgrading my ubuntu server from 8.04 to 10.04 and then to 10.10, grub failed to load and showed a:
L 99 99 99 99 99 99 99 99 ....

I restarted using a liveCD, mounted my boot partition as /boot and then "grub-install /dev/sdb" (sda is the usb drive now) so I have access to grub console, but I don't know how to recover my boot menu.

I also use LVM, but I don't know if this is relevant.

Any hint? thanks

---

### Post by sikander3786 on 2010-11-10
Please boot into a LiveCD and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us better understand your current situation as thus help you accordingly. Please wrap the output with proper code tags # from the post menu.

---

