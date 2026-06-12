---
title: "Installing Ubuntu on Nexus 7 issue"
date: 2016-01-06
forum: Ubuntu Phone and Tablet
---

### Post by j-desanto0 on 2016-01-06
I've been trying to install Ubuntu Touch on my daughter's old Nexus7 2012 edition and I get to the point where I should install and this happens:

```
ubuntu-device-flash touch --channel=ubuntu-touch/stable/ubuntu --bootstrap2016/01/06 08:57:52 Expecting the device to be in the bootloader... waiting
2016/01/06 08:57:52 Device is |grouper|
Device grouper not found on server https://system-image.ubuntu.com channel ubuntu-touch/stable/ubuntu

```

All the guides say the device is |mako| not |grouper| and it won't let me continue from there.

---

### Post by philhughes on 2016-01-06
Nexus 7 2012 is grouper and is not supported. Mako is Nexus 4.

[https://developers.google.com/android/nexus/drivers](https://developers.google.com/android/nexus/drivers)
[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

---

### Post by j-desanto0 on 2016-01-06
> **philhughes said:**
> Nexus 7 2012 is grouper and is not supported. Mako is Nexus 4.

[https://developers.google.com/android/nexus/drivers](https://developers.google.com/android/nexus/drivers)
[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

Well, that sucks.  Useless piece of hardware then.  Yay.

---

