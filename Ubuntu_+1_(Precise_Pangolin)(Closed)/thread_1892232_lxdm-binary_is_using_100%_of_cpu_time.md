---
title: "lxdm-binary is using 100% of cpu time"
date: 2011-12-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Sworddragon on 2011-12-07
Today I have rebooted my system after ~1 day and lxdm-binary from root is using constantly 100% of cpu time. I can't figure out why this happens. Has somebody else the same problem? Is this maybe a bug of a new package?


Edit: I figured out that this problem appeared after upgrading to libglib2.0-0 2.31.2-0ubuntu1. gksu with PCManFM isn't working correctly too after this upgrade. Downgrading libglib2.0-0 will solve the problem but break the system.


Edit2: [Here](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/901407) is the bug report.

---

