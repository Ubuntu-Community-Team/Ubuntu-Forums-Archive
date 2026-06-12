---
title: "Ubuntu Touch on no longer supported devices."
date: 2015-05-08
forum: Ubuntu Phone and Tablet
---

### Post by pantera989 on 2015-05-08
Trying to get Ubuntu to work on an older Nexus 7 (Grouper) that's no longer supported. 

I originally tried installing from Ubuntu desktop but failed at the ```
$ ubuntu-device-flash touch --channel=devel --bootstrap
``` step (tried some other channels a swell) and jsut got the message "Device grouper not found on server" which I'm assuming is because it's no longer supported.

I found a guide on manually downloading the .img file etc which seemed to send fine to the tablet with the following command:

```
fastboot flash boot /*.img
```

The instructions where to then go to recovery mode to load the sideloader .zips but when I got to recovery it just gives the lying down robot with an red !

Any ideas waht I've done wrong (I'm not to worried about the device itself, it was an old one lying around)

---

### Post by lgd on 2015-05-09
Recovery mode is not starting until you see the menu? Have you seen it before a day?

I think it was a very bad idea to flash all (*) images to only the boot partition "boot". Can you start fastboot or the recovery or normal system or is all dead?

---

