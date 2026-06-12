---
title: "Minimized games are still visible on X.Org 1.15.0"
date: 2014-02-13
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2014-02-13
As described in [this](https://bugs.freedesktop.org/show_bug.cgi?id=74651) report if I'm minimizing an application that has initialized OpenGL and is in fullscreen mode it will still show the last frame on the desktop. The bug report also contains an example screenshot. I'm not seeing any threads here about this issue so I'm assuming it could be a hardware or a configuration issue. /var/log/Xorg.0.log doesn't contain any differences about warnings compared with X.Org 1.14.5. This bug would be a major system breakage for me if this state is going into 14.04 final. Does somebody know about this bug or has any idea?

---

