---
title: "Wireless WPA/WPA2 Personal not connecting"
date: 2013-03-10
forum: Ubuntu Development Version
---

### Post by zerubbabel on 2013-03-10
I'm running Kubuntu 13.04 Alpha 2 (with all updates applied) on a Dell Latitude which has a Broadcom BCM4313 Wireless LAN controller. I am able to connect to unsecured WiFi connections with no problem, but not to my Belkin wireless router which is configured for WPA/WPA2 Personal wireless security. However, just before I installed 13.04, I was running 12.10 and was able to connect to this same network with no problem, using the same key, which has not been changed. I am wondering whether anyone else has run into a problem like this.

---

### Post by cariboo on 2013-03-10
What driver are you using?

---

### Post by zerubbabel on 2013-03-10
It was using the proprietary Broadcom driver. When I removed that driver, it connected.

---

### Post by cariboo on 2013-03-10
> **zerubbabel said:**
> It was using the proprietary Broadcom driver. When I removed that driver, it connected.

There are several proprietary Broadcom drivers, I used bcmwl-kernel-source, on my netbook with a BCM4312 chipset, this is the same driver that is listed for your chipset. If you have the media you installed from, you can install the driver without a working network connection. You need to install dkms and fakeroot before you install the driver, they are located in pool/main/d/dkms and pool/main/f/fakeroot. To install them, in a terminal:

```
cd /pool/main/d/dkms
```

then 

```
sudo dpkg -i *deb
``` 

for fakeroot:

```
cd /pool/main/f/fakeroot
```

then

```
sudo dpkg -i *deb
```

after the above two packages have installed successfully:

```
cd /pool/restricted/b/bcmwl
```

then

```
sudo dpkg -i *deb
```

reboot, and when you are back at the desktop, you should have a reliably working wifi connection

---

### Post by zerubbabel on 2013-03-12
Thank you very much for the detailed instructions, but I'm just wondering, since the generic driver works after disabling the previously installed Broadcom driver, what advantage is there in installing a different proprietary Broadcom driver?

---

### Post by cariboo on 2013-03-12
If it works, don't do anything. during previous development cycles we found that some of the chipsets (BCM4311, BCM4312 and BCM4313) use the wl driver, and others used the b43 driver, depending on the version. We really didn't try to track version numbers, as we just wanted to get every one working properly, and since then it really hasn't been much of an issue, so it wasn't pursued any further.

---

### Post by ping-wu on 2013-03-12
My experience is the same: Don't use the proprietary BCM driver.  The default (open-sourced?) drivers works just fine.

---

