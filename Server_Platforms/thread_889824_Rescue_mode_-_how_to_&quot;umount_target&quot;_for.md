---
title: "Rescue mode - how to &quot;umount /target&quot; for resizing lvm"
date: 2008-08-14
forum: Server Platforms
---

### Post by whosmatt on 2008-08-14
Running 8.04 LTS on Dell PV500 NAS device.  I have LVM and I have resized my root lv and want to resize the filesystem as well to take advantage of the new space.  I'm using the rescue mode but am unable to unnmount the filesystem. "umount /target" returns an error "Inappropriate ioctl for device"  "umount -f /target" just returns "forced umount of /target failed!"

any suggestions?  apparently rescue mode forces one to mount a root filesystem and this is my only mountable media.

---

### Post by dca on 2008-08-14
When LVM2 is active on your box you shouldn't need to log into recovery mode unless something is broke, not to re-size.
 
This how-to is what I used for messing around w/ LVMs...
 
[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

---

### Post by windependence on 2008-08-15
dca is correct here, but for future reference you can try a lazy umount

```
umount -l /target
```


if the forced umount doesn't work which is most of the time. :)

Great How To dca, THANKS!

-Tim

---

