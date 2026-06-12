---
title: "a problem regarding BIOS setup"
date: 2014-09-09
forum: System76 Support
---

### Post by rodrigo-manzo on 2014-09-09
recently my laptop screen broke, so i was forced to use a led tv as monitor meanwhile, the computer starts normally, but for some reason the BIOS date and time setting are off, i know because many of my windows app use that time instead of the one i provide to the windows config, more so im getting constant domain certificate issues as the date of those is different from that in the BIOS.

The problem is that, the video card (ati radeon) won't send any signal to the tv (both for hdmi and vga) till after the lightdm or the windows start screen appears, which means i can access BIOS, but can't see any part of it clearly as it's displayed on the laptop screen.

I was wondering if there is a way to change BIOS settings from within the Ubuntu environment as i know that kind of functions can't be done from windows

---

### Post by ibjsb4 on 2014-09-10
Bios boots before the operating system, whether it be linux or windows.

---

### Post by monocell on 2014-09-10
I'm suprised ntpd doesn't set the correct time automatically. You can try to run `hwclock --systohc` to set the bios time. `hwclock` will also tell you current bios time if that is of interest.

---

