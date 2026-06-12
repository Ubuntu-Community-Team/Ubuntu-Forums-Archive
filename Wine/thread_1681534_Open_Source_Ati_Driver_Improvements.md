---
title: "Open Source Ati Driver Improvements"
date: 2011-02-04
forum: Wine
---

### Post by dh04000 on 2011-02-04
[http://www.phoronix.com/scan.php?pag...expanded&num=1](http://www.phoronix.com/scan.php?pag...expanded&num=1)

The Gallium Driver is 75%(in most of the tests) of what the catalyst driver was in 2008. I seem to remember wine and tf2 work for me in Hardy. So, does anyone know if this newest driver supports wine? Can I go back to working TF2 in ubuntu?

Has anyone tested this?

---

### Post by cogadh on 2011-02-04
The driver doesn't support Wine in the first place. Wine will always make use of whatever graphics driver you are currently using, no matter what. If the driver is not fully featured and is lacking some OpenGL functions, then some of Wine's functions may not work correctly, but that is not a lack of support for Wine, that is a lack of OpenGL support.

---

### Post by brookie on 2011-02-04
They will be powered by turbo-hamsters right? :) 

[IMG]http://img84.imageshack.us/img84/5923/cutehamster.jpg[/IMG]

Happy Friday! Hee hee.

---

### Post by CarpKing on 2011-02-06
As stated above, the key is which OpenGL functions the driver provides.  The OSS radeon driver has been gaining better OpenGL support through Gallium3D.  Is your card one of those that is no longer supported by the Catalyst driver?  If so, Gallium should be up to the speed of non-Gallium by now, and have much better OpenGL support.  If you want to give it a shot and are willing to live a bit on the wild side, you could try the xorg-edgers repository.  

If you aren't brave enough for bleeding edge packages, you might try again with stock Maverick packages.  I *think* Maverick defaults to Gallium for r300-r500 cards, but if not you can enable it.  This would give you many but not all of the OpenGL improvements seen in the new driver.

---

### Post by handy on 2011-02-06
Some may find post #1911 here:

[https://bbs.archlinux.org/viewtopic.php?pid=888202#p888202](https://bbs.archlinux.org/viewtopic.php?pid=888202#p888202)

Useful.

I'd also recommend using the xorg-edgers ppa, as the driver stack, kernel are in great shape.

---

