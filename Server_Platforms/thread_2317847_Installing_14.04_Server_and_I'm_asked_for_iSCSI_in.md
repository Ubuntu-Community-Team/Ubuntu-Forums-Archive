---
title: "Installing 14.04 Server and I'm asked for iSCSI info.?"
date: 2016-03-20
forum: Server Platforms
---

### Post by xhmdr-patngm-etf3e on 2016-03-20
I had an old Mac Mini (2009) that broke from an update. I keep getting the error Apple shows when the internal drive can not be read. I figured the update simply corrupted the OS and decided to turn it in to a little dedicated i2p server. However, when I attempt to install Ubuntu Server 14.04 from USB it doesn't show drives, it just asks me for iSCSI information. Isn't iSCSI used to link storage together? Does this mean it was not the update that ruined the Mac Mini storage? What is causing it, ruined drive or drive cable? Or is the drive just kind of "locked out" with Apple?

---

### Post by mastablasta on 2016-03-20
use SMART tools to diagnose the drive first. it maybe that it failed. i am not sure how this is done on Apple, but on PC the ultimate boot CD has such tools. probably a few others out there on the web as well.

---

### Post by xhmdr-patngm-etf3e on 2016-03-20
Would it be possible to check this from a Live version of Ubuntu or other Linux distro? It would be easier because I already have Ubuntu on USB.

edit

[Yeah]("https://help.ubuntu.com/community/Smartmontools"), I'll just do it from my Ubuntu USB. 
I hate dealing with all of Apple's proprietary locked out stuff. I have no idea if this is a standard Apple feature or if the drive failed, and I'm not about to take it to an Apple store and pay for support.

---

