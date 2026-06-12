---
title: "App Armor + Chromium"
date: 2013-07-11
forum: Security
---

### Post by steelcat on 2013-07-11
Hello guys. Kindly asking to get a hand to solve the issue with the web cam using restriction for Chromium.

When browser starts, it reads:
/sys/bus/pci/devices/ r,
/sys/bus/pci/devices/*/resource r,
/sys/devices/pci0000:00/** r,

One of the devices is webcam which I want to close the access for Chromium.

There is the case, once the access to camera is closed by AppArmor Chromium exiting writing the message: "Access denied".

It would be nice, if some one could show me even the direction to work this issue out.

Thank you in advance.

P.S. rmmod is not the solution.

---

