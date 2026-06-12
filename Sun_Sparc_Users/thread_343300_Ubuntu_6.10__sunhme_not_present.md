---
title: "Ubuntu 6.10 : sunhme not present ?"
date: 2007-01-21
forum: Sun Sparc Users
---

### Post by ultrabill on 2007-01-21
Hello,

I'm running U6.10 on my great Ultra1. Everything is all right except my sbus ethernet card which requiere the "sunhme" module. Debian have this module because I could use this card with it ... not with Ubuntu.

Of course, the internal Ethernet card is ok but it's 10Mbps only :frown: 

So, what should I do ? Say goodbye to Ubuntu :-k

---

### Post by Moulton on 2007-02-03
I have found that the 64-bit version of Sparc Linux doesn't have good support for S-Bus cards.  The S-Bus drivers that work fine in the 32-bit Debian Sparc distros don't seem to work properly in the 64-bit Ubuntu distros.  I had to procure a UPA Creator card because the X.Org drivers didn't work correctly with the S-Bus CGsix Graphic adaptor on 64-bit Ubuntu Linux.  One exception is S-Bus SCSI-3 adaptor.  That one does work in 64-bit Ubuntu.

---

