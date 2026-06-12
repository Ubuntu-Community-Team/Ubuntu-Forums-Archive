---
title: "System76 Starling Ad-Hoc Issues"
date: 2009-06-15
forum: System76 Support
---

### Post by kingnerd on 2009-06-15
The System76 Starling is not able to go into ad-hoc wireless mode.  Networkmanager is perpetually configuring, and when tried manually, a sudo ifconfig wlan0 up yields

```
SIOCSIFFLAGS: Operation not supported
```

Any ideas?  I need this feature do to tethering requiring it.

---

### Post by thomasaaron on 2009-06-16
I'd try to get this bug report going again.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/97322](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/97322)

Looks like there hasn't been any progress in getting ad hocs working on this wifi adapter for a while.

---

