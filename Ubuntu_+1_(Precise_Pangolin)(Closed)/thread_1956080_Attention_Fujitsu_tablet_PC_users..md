---
title: "Attention Fujitsu tablet PC users."
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Favux on 2012-04-10
[SIZE="3"][COLOR="Blue"]A call for Fujitsu tablet PC testers![/COLOR][/SIZE]

Robert Gerlach's new **fujitsu-tablet.ko** has been accepted into the 3.3 kernel.  Amongst other things it provides notification of whether the screen is physically in laptop or tablet mode/orientation.  And yes, this is the Robert Gerlach of the **fjbtndrv PPA**.

**Magick Rotation** is an application that will automatically change screen orientation and input tool (stylus, touch) orientation when you physically rotate the screen.  With Robert's assistance Fujitsu tablet PC's have been added to Magick but the support needs testing.

A DKMS implementation of the fujitsu-tablet.ko is in the MagickExtras folder along with instructions so the driver can be used with older kernels in Ubuntu releases including Precise.  The included version of fujitsu-tablet.c (4-4-12) also has Robert's new patch that fixes tablet state reporting for some models (should be in the 3.4 kernel) and another patch from Robert that allows it to build down to the 2.6.32 kernel (Lucid's).

Magick Rotation is here:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)
Revision 45 on the devel branch is the testable version of Magick with a dkms of fujitsu-tablet.ko.  It's tarball is here:  [http://bazaar.launchpad.net/~magick-admin-team/magick-rotation/devel/tarball/45](http://bazaar.launchpad.net/~magick-admin-team/magick-rotation/devel/tarball/45)
To install drill down to the devel folder and run MAGICK-INSTALL.  It should be executable.  As mentioned the dkms package and instructions are in the MagickExtras folder.  You can remove Magick with MAGICK-UNINSTALL in the MagickUninstall folder.

Please post your results if you do test.

Thank you,

Favux

---

### Post by teh603 on 2012-04-10
Is this like the accellerometer in the Dell Inspiron Duo?

---

### Post by Favux on 2012-04-10
Hi teh603,

No, this is the swivel hinge switch signal of convertible tablet PC's.

We've discussed adding accelerometer support but haven't done so yet.  Some folks with iPad type slates do use Magick for xrotate.py.

---

