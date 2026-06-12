---
title: "Does anyone have experience with flashing a phone to Ubuntu Touch?"
date: 2015-03-01
forum: Ubuntu Phone and Tablet
---

### Post by bartveurink5 on 2015-03-01
Does anyone have experience with flashing a phone to Ubuntu Touch?
Where should I be careful not to damage my phone?
It is a HTC Desire S with Android 2.3

---

### Post by gifford on 2015-03-01
You should look at Mobile Technology Discussions on this site or XDA developers for the information you are looking for.

---

### Post by bartveurink5 on 2015-03-01
HTC Flash Phone Touchy phone to ubuntu Touch. It is a HTC Desire S.
What is important to not damage my phone? Are the images well tested and trusted? How to use the ubuntu-device-flash for correct flashing?

---

### Post by grahammechanical on 2015-03-01
You will need a port for your device

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

> [COLOR=#333333][FONT=Ubuntu]Ubuntu for devices is still under development. Installing an Ubuntu for devices image may make your device unusable. Important features may be missing or broken. New images may introduce new features and may break existing features as development continues. Ubuntu for devices does not yet provide a reliable replacement for your current handset, phone or tablet.[/FONT][/COLOR]

The developers are testing Ubuntu for Devices (Touch) on 3 reference devices - Nexus 4; Nexus 7 (2013) and Nexus 10. I would have some confidence flashing Ubuntu for Devices on one of those 3 devices. But any other devices I would have much less confidence. To put it another way. I would not risk it.

Regards.

---

### Post by ian-weisser on 2015-03-01
See [https://developer.ubuntu.com/en/start/ubuntu-for-devices/porting-new-device/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/porting-new-device/)

I don't think anybody has tested that model. You will be breaking new ground!

---

### Post by Bucky Ball on 2015-03-01
***Threads merged.***

Please do not duplicate post.

---

### Post by bartveurink5 on 2015-03-02
adb does return this. How to give permission?

```
$ adb devices* daemon not running. starting it now on port 5037 *
* daemon started successfully *
List of devices attached 
????????????    no permissions



```

---

### Post by bartveurink5 on 2015-03-02
I got the answer on: [http://stackoverflow.com/questions/14460656/android-debug-bridge-adb-device-no-permissions](http://stackoverflow.com/questions/14460656/android-debug-bridge-adb-device-no-permissions)

---

### Post by bartveurink5 on 2015-03-02
I still got permission denied when I try to return image type, device type and build ID

---

### Post by bartveurink5 on 2015-03-02
Error here:
```
$ sudo fastboot oem unlock...
(bootloader) [ERR] Command error !!!
OKAY [  0.004s]
finished. total time: 0.004s
```

Tap build number seven times doesn't work. Is this the reason that permission is denied?

---

### Post by bartveurink5 on 2015-03-02
a problem with connecting:
```
$ sudo adb backup -apk -shared -all
adb: unable to connect for backup
```

---

### Post by schankame on 2015-03-22
You did root the device first right? I just want to make sure. I ran in to the same problem when my root didn't complete on my Samsung Google Nexus.

---

