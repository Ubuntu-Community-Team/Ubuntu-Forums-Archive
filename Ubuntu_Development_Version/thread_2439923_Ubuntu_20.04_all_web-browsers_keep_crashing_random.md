---
title: "Ubuntu 20.04 all web-browsers keep crashing randomly"
date: 2020-04-03
forum: Ubuntu Development Version
---

### Post by MasterCATZ on 2020-04-03
[COLOR=#000000][INDENT]ever since I went from 19.10 to 20.04 , chrome based browsers and firefox keep randomly crashing


where is best place to report this and what information / debugging should I do >?
I am leaning towards possibly GPU acceleration


crashes from /var/crash 

[https://drive.google.com/open?id=1sjbSaB_jcJ19M0cl-94S8Tz_BY4sQiXx](https://drive.google.com/open?id=1sjbSaB_jcJ19M0cl-94S8Tz_BY4sQiXx)[/INDENT]
[/COLOR]

---

### Post by slickymaster on 2020-04-03
*Thread moved to **Ubuntu Development Version**.*

---

### Post by lvm on 2020-04-03
Firefox doesn't support GPU acceleration on linux ([https://bugzilla.mozilla.org/show_bug.cgi?id=1210726](https://bugzilla.mozilla.org/show_bug.cgi?id=1210726)) so it can't be that, not directly anyway. The proper place for reporting ubuntu bugs is [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by Sophont on 2020-04-07
> **lvm said:**
> Firefox doesn't support GPU acceleration on linux ([https://bugzilla.mozilla.org/show_bug.cgi?id=1210726](https://bugzilla.mozilla.org/show_bug.cgi?id=1210726)) so it can't be that, not directly anyway. The proper place for reporting ubuntu bugs is [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

Actually it does - you just have to enable it. Did that a long time ago without any issues so far:
[https://cialu.net/enable-hardware-acceleration-firefox-make-faster/]("https://cialu.net/enable-hardware-acceleration-firefox-make-faster/")

---

### Post by dino99 on 2020-04-07
As you have made a dist-upgrade, keep in mind to do a system cleaning via clean/autoclean/autoremove/bleachbit to get rid of old packages/settings that could disturb the system.
Also test possible conflict related with third party source(s); in such a case, disable/downgrade those; and the reboot and glace at journalctl after a new crash (if that happen)

---

