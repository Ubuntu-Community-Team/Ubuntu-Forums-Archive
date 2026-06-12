---
title: "scrolling (smooth) has degraded with new gtk3 build (unity session"
date: 2013-04-21
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-04-21
At least as seen here, most noticeable on laptop with touchpad & in large doc's in gedit.
(bit ironic as latest build was meant to fix some scroll issues, somewhere, not here 
Reverting to previous gtk3* returns scrolling to previous good performance ((3.6.4-0ubuntu6
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1171156](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1171156)

---

### Post by mc4man on 2013-04-22
resolved to some extent,may make release, may be after.
It appears to only affect a unity session & appears in a somewhat limited fashion 

Edit:fix was released now (previous patch reverted

---

### Post by mc4man on 2013-06-14
As not unexpected has returned in 3.8, seems to have gotten worse lately
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1184159](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1184159)

---

### Post by ventrical on 2013-06-15
Absolutely terrible scroll performance in firefox web browser on standard desktop.

Edit:

Not sure if this has to do with gtk+3 bug. Just noticed it now.

---

### Post by xeizo on 2013-06-15
> **ventrical said:**
> Absolutely terrible scroll performance in firefox web browser.  Works fine here, smooth, but I'm using the Nvidia-blob again and a fairly powerful  gpu in the GTX650Ti. Yesterdays Ubuntu-daily updated to todays and with ubuntu-gnome-desktop slammed on it using Gnome-Shell and todays daily 3.10-kernel .... a lot of things are very buggy at this stage in the cycle though ...

---

### Post by mc4man on 2013-06-15
> **ventrical said:**
> Absolutely terrible scroll performance in firefox web browser on standard desktop.

Edit:

Not sure if this has to do with gtk+3 bug. Just noticed it now.
Probably not, & just to note as current bug report may not may clear - this just affects a unity session, not gnome-shell

---

### Post by ventrical on 2013-06-15
I am using Unity.

Restart after update fixed problem.

---

