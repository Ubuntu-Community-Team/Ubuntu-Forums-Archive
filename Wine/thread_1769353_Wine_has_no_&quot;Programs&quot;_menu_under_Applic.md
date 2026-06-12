---
title: "Wine has no &quot;Programs&quot; menu under Applications"
date: 2011-05-27
forum: Wine
---

### Post by 3602 on 2011-05-27
Wine version: 1.2.2 according to winecfg.
Ubuntu version: Ubuntu 10.10 Maverick Meerkat 64-bit
```
$ uname -a
Linux $USER-dv7 2.6.35-29-generic #51-Ubuntu SMP Fri Apr 15 17:12:35 UTC 2011 x86_64 GNU/Linux

```The problem is that Windows programs install fine under Wine, but they don't show up in the usual Programs menu when I go Applications -> Wine. There is simple no "Programs" menu.
More info: I previously had the 1.3 beta version, I had it removed (purged) and installed the 1.2. I have removed the hidden .wine after removing the 1.3 install.

Thank you very much.

---

### Post by 3602 on 2011-05-27
Solved by doing the exact following (time capsule for my future self):
Uninstall CrossOver
Fully uninstalling CrossOver
removing everything marked "wine" in .config/menus and .local/shared/applications/something like that.
Purge wine 1.2
Install wine 1.3

---

