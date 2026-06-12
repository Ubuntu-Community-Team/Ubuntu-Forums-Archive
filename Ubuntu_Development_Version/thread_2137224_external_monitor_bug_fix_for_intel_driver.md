---
title: "external monitor bug fix for intel driver"
date: 2013-04-20
forum: Ubuntu Development Version
---

### Post by ft_ on 2013-04-20
I noticed this good bug fix last night :

> xserver-xorg-video-intel (2:2.21.6-0ubuntu4) raring-proposed; urgency=low

  [Chris Arges]
  * Add sna-flush-scanout-cache-after-resizing.patch: Flush the scanout
    cache after resizing the display.  Fixes a problem that occurs
    e.g. when unplugging an external display, suspend/resume, etc. by
    ensuring the scanout cache is properly sized.
    (LP: #1157678)
 -- Bryce Harrington <bryce@ubuntu.com>   Fri, 19 Apr 2013 11:12:14 -0700

---

### Post by screaminj3sus on 2013-04-20
awesome, ran into this bug the other day glad its fixed.

---

