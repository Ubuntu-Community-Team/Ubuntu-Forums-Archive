---
title: "USB-modeswitch held back"
date: 2011-11-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-11-04
I installed a USB 3.0 PCI Express card about  a month ago. I had one problem so far in that it would not properly mount a pendrive. Now I get this:  any ideas?

---

### Post by cariboo on 2011-11-04
That should have nothing to do with your PCI card, it's for usb WAN dongles

---

### Post by mc4man on 2011-11-04
As far as the upgrade - changelogs can prove informative - 
> usb-modeswitch-data (20110805-1) unstable; urgency=low

  * New upstream release
......
 * Bump usb-modeswitch relationships to >= [COLOR="Blue"]1.2.0[/COLOR].

---

### Post by jfernyhough on 2011-11-04
> **ventrical said:**
> Now I get this:  any ideas?Packages that are held back normally means they have dependencies that aren't met, for example usb-modeswitch depends on usb-modeswitch-data. If one updated package has been pushed but one has not the depending package will be held.

---

### Post by ventrical on 2011-11-05
Thanks everyone for your help on this.

---

### Post by JRV on 2011-11-06
I just did an update and it has been fixed.

14:30 GMT - Nov 6,2011

---

### Post by ventrical on 2011-11-06
Thanks!

---

