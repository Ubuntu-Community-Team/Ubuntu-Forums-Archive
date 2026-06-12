---
title: "udev rules to detect USB device removal"
date: 2015-07-10
forum: Ubuntu Development Version
---

### Post by lyf on 2015-07-10
Hi Experts,

Is there any sample udev rules file to detect the removal of the USB device ?

In my rules file the device arrival action is detected with respect to VID/PID and other informations but removal I am not able to match VID/PID since the information will be lost once the device is removed.

Regards,
Lyf

---

### Post by dino99 on 2015-07-10
what do you want/try to do ? the system already has that hotplug feature and automaticaly deals with plug/unplug.
what is the relationship with Wily subforum?
[http://manpages.ubuntu.com/manpages/vivid/en/man8/udevadm.8.html](http://manpages.ubuntu.com/manpages/vivid/en/man8/udevadm.8.html)

---

