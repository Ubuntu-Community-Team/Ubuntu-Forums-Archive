---
title: "Ubuntu GNOME upgrade won't wake from suspend"
date: 2018-03-12
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2018-03-12
I decided to have a look at how the Ubuntu GNOME 16.04 -> Ubuntu 18.04 upgrade process would work and encountered one problem that has me scratching my head. It seems that Ubuntu GNOME by default has suspend set to on and once the upgrade process is complete suspend is still set to on (after 20 minutes I think). In Ubuntu 18.04 I believe suspend is set to off by default.

What happens is that the freshly upgraded UG 16.04 -> Ubuntu 18.04 simply refuses to wake from suspend using a USB keyboard/mouse. On my desktop PC I can plug in a PS2 mouse and keyboard and then wake from suspend works fine. Or on my Latitude E6400 I can simply use the laptops own keyboard/touchpad to wake from suspend.

My personal "fix" is to simply set suspend to off and then it's not an issue. But I wonder, since Ubuntu's default is having suspend set to off out-of-box, if an Ubuntu GNOME 16.04 -> Ubuntu 18.04 should also adopt that default? I don't mind filing a bug report if need be, but I'm pretty sure that's a well known GNOME behavior. In some cases BIOS settings can be tweaked to correct the wake from USB behavior but I prefer to just not suspend at all.

---

### Post by kansasnoob on 2018-03-12
Unrelated to that issue but the only two actual bugs encountered in that upgrade process were:

[https://bugs.launchpad.net/plymouth/+bug/927636](https://bugs.launchpad.net/plymouth/+bug/927636)

[https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/1751460](https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/1751460)

---

