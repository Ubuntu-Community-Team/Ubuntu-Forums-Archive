---
title: "No login screen: Failed to initialize glamor at ScreenInit() time."
date: 2015-03-15
forum: Ubuntu Development Version
---

### Post by 0x656b694d on 2015-03-15
Hello,

The login screen disappeared on my Asus eeePc. Interestingly, with the same 15.04 + xorg-edgers I have everything working fine on my desktop computer.

The Xorg.0.log on the problematic machine:

```
[    36.205] (II) Loading /usr/lib/xorg/modules/libfb.so
[    36.205] (II) Module fb: vendor="X.Org Foundation"
[    36.205]    compiled for 1.17.1, module version = 1.0.0
[    36.205]    ABI class: X.Org ANSI C Emulation, version 0.4
[    36.205] (II) UnloadModule: "vesa"
[    36.206] (II) Unloading vesa
[    36.206] (==) Depth 24 pixmap format is 32 bpp
[    36.207] Require OpenGL version 2.1 or later.
[    36.207] (EE) modeset(0): Failed to initialize glamor at ScreenInit() time.
[    36.207] (EE) 
Fatal server error:
[    36.207] (EE) AddScreen/ScreenInit failed for driver 0

```

Any ideas? I tried to purge xorg-edgers, but it didn't help.

Thanks in advance!

---

### Post by 0x656b694d on 2015-03-23
I've reinstalled from daily iso and the issue is gone.

---

