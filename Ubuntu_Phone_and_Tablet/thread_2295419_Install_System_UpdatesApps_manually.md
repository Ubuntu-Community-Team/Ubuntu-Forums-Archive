---
title: "Install System Updates/Apps manually"
date: 2015-09-18
forum: Ubuntu Phone and Tablet
---

### Post by ubogreg on 2015-09-18
Hi ubuntu phone experts,  I'd like to install System Updates/Apps manually on my Aquaris E4.5 Ubuntu Edition using terminal access and adb connection. Unfortunately I don't have always access to the internet on my phone (sometimes for security reasons, bandwidth limitations and other limitations).   But I have a PC to download System Updates/Apps and transfering can be done using adb connection and USB.  Now my problems is: how can I install those System Updates/Apps manually using terminal access?      Any help would be gratefully appreciated.    Greg

---

### Post by grahammechanical on 2015-09-18
You may need to re-flash the OS. Or re-flashing may be the way to do it.  I do not have a Ubuntu Phone and I would not experiment with a device  that I had paid good money for, anyway. But it is up to you.

[http://askubuntu.com/questions/602035/how-do-i-use-ubuntu-device-flash-with-the-bq-aquaris-e4-5-and-aquaris-e5](http://askubuntu.com/questions/602035/how-do-i-use-ubuntu-device-flash-with-the-bq-aquaris-e4-5-and-aquaris-e5)

Regards.

---

### Post by ubogreg on 2015-09-18
Re-flashing the OS does not install an app manually. Maybe standard apps will be installed. But I don't want to use only standard apps.    And the ubuntu-device-flash command expects a channel to download from, but I don't have access to [https://system-image.ubuntu.com](https://system-image.ubuntu.com).     > **grahammechanical said:**
> You may need to re-flash the OS. Or re-flashing may be the way to do it.  I do not have a Ubuntu Phone and I would not experiment with a device  that I had paid good money for, anyway. But it is up to you.  [http://askubuntu.com/questions/602035/how-do-i-use-ubuntu-device-flash-with-the-bq-aquaris-e4-5-and-aquaris-e5](http://askubuntu.com/questions/602035/how-do-i-use-ubuntu-device-flash-with-the-bq-aquaris-e4-5-and-aquaris-e5)  Regards.

---

### Post by qduaty on 2015-10-14
Use **dpkg** for system updates and **pkcon install-local** for apps.

---

