---
title: "Firefox fails to load XPCOM components"
date: 2009-07-03
forum: Software
---

### Post by minj on 2009-07-03
I'm not sure when exactly it started but I guess it was after some of the xulrunner/FF updates. These 2 lines keep looping in FF error console (even in -safe-mode):

```
Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.11/components/libpyloader.so
Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.11/components/pyabout.py
```

Oh and yeah, those 2 files exist :P

At first I neglected them but it seems to affect whole system's performance more and more. Now when I open Add-ons and especially try to change their preferences firefox goes sky high to 90%+ CPU.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.11) Gecko/2009060308 Ubuntu/9.04 (jaunty) Firefox/3.0.11

Any ideas? :(

---

### Post by aledruetta on 2009-07-03
ai dont spik ingliy (se nota ¿verdad?) sorri

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/386845](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/386845)

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1534732.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1534732.html)

---

