---
title: "Problem with Kernel 3.13.0-20-generic on Intel graphics"
date: 2014-03-29
forum: Ubuntu Development Version
---

### Post by Gavin77 on 2014-03-29
```
Graphics:  Card: Intel 4 Series Integrated Graphics Controller 
           X.Org: 1.15.0 drivers: intel (unloaded: fbdev,vesa) Resolution: 1440x900@59.9hz 
           GLX Renderer: Mesa DRI Intel G41 GLX Version: 2.1 Mesa 10.2.0-devel
```

I performed an update today and upon rebooting lost all desktop effects and Kwin was crashing repeatedly upon trying to enable effects.  In the end I reinstalled a backup of my system from a few days ago and all was working again.

I've narrowed the problem down to the new kernel as rebooting into the previous one (3.13.0-19-generic) works fine.

Looking at the changelog for 3.13.0-20, I see lots of references for Intel pointing to this bugfix [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1294144](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1294144) I wonder if that has broken something on non Broadwell chips?

---

### Post by Gavin77 on 2014-03-29
Looks like I'm not alone, someone else has just reported the same thing [https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1299499](https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1299499)

---

