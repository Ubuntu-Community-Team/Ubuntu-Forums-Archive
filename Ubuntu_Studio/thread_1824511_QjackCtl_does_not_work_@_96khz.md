---
title: "QjackCtl does not work @ 96khz ?"
date: 2011-08-13
forum: Ubuntu Studio
---

### Post by JuanPabloCuervo on 2011-08-13
Hi,

if Sample Rate is 44.1khz.. QjackCtl 0.3.8 does work...
MeterBridge too,
but if Sample Rate in hdspconfig is 96khz...
:guitar:
[SOLVED] 
Channel count at 96khz is 8I 8O. with RME HDSP9632 or AIO.
at 48khz is 12i 12o
it was set to Manual 12 not (Default).
@192khz is 4i 4o.
just needed some sleep.

[http://qjackctl.sourceforge.net/#Support](http://qjackctl.sourceforge.net/#Support)
[http://sourceforge.net/projects/qjackctl/support](http://sourceforge.net/projects/qjackctl/support)

---

