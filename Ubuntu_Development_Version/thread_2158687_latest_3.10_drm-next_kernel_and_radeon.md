---
title: "latest 3.10 drm-next kernel and radeon"
date: 2013-06-30
forum: Ubuntu Development Version
---

### Post by deadite66 on 2013-06-30
installed the the latest [2013-06-29-saucy]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/2013-06-29-saucy/") build and enabled radeon.dpm=1 in grub.

loving it, full speed desktop and low fan noise, i've lost vmware support (can't compile all the modules) but worth it.

using a HD6970 on my desktop, doesn't seem to work on my e350 APU mini-itx machine though i get a black screen.


```
lee@kubuntu:~$ dmesg |grep dpm
[    1.532151] [drm] radeon: dpm initialized

```

[AMD Has Massive Radeon Patch Set - Power Management!]("http://www.phoronix.com/scan.php?page=news_item&px=MTM5NjE")

---

### Post by zika on 2013-06-30
> **deadite66 said:**
> installed the the latest [2013-06-29-saucy]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/2013-06-29-saucy/") build and enabled radeon.dpm=1 in grub.

loving it, full speed desktop and low fan noise, i've lost vmware support (can't compile all the modules) but worth it.

using a HD6970 on my desktop, doesn't seem to work on my e350 APU mini-itx machine though i get a black screen.


```
lee@kubuntu:~$ dmesg |grep dpm
[    1.532151] [drm] radeon: dpm initialized

```

[AMD Has Massive Radeon Patch Set - Power Management!]("http://www.phoronix.com/scan.php?page=news_item&px=MTM5NjE")
[http://forum.ubuntu-rs.org/Thread-ubuntu-13-10-codename-saucy-salamander?pid=223432#pid223432](http://forum.ubuntu-rs.org/Thread-ubuntu-13-10-codename-saucy-salamander?pid=223432#pid223432)
Works nice for couple of days...
Feels like 3.11 already... ;)

Forgot to write: You do not need 3.11 to have dpm...
```
/bin/echo "dynpm" > /sys/class/drm/card0/device/power_method
```for year(s) now...

---

