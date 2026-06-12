---
title: "Lost mouse pointer with Realtime Kernel"
date: 2010-04-25
forum: Ubuntu Studio
---

### Post by bikodog on 2010-04-25
Whenever I boot the realtime kernel 2.6.28-3-rt my mouse pointer is missing. As I move it around I can see it "ghosting" over icons and panels, and it it works fine - it is just missing from the display.

Reboot into plain-vanilla kernel 2.6.28-18-generic and it's there.

anyone have any ideas?

---

### Post by sgx on 2010-04-25
Hi, in the old days, you could add this line to xorg.conf

Option "HWCursor" "off"

likely the last line of the mouse section.
Can't guarantee it, but its a maybe :)

this was due to a bug in some nvidia drivers

---

### Post by bikodog on 2010-04-27
thanks sgx.

so here's a question, is there a different xorg.conf for each kernel?

---

### Post by trulan on 2010-04-27
No, there's only one xorg.conf.  In the past I have used a startup script to copy in the xorg.conf I wanted, based on custom menu entries in grub - it worked but it was a pain.  (the purpose was to select or de-select the nvidia driver, due to another bug in the driver)

I cut my Linux teeth on the 2.6.28-3-rt kernel.  To be honest, I'm glad to be rid of the thing.  One of my machines would hang on it in a matter of seconds after booting, and another would hang 2 out of three times while attempting to load the nvidia driver.  2.6.31-rt from Karmic is WAY better IMO...

---

### Post by sgx on 2010-04-29
> **bikodog said:**
> thanks sgx.

so here's a question, is there a different xorg.conf for each kernel?
The xorg.conf file is produced by the brains  of the computer, based on
the hardware detection implementation used. The file itself can be perfect,
or useless, depending on the video chip/card, monitor, mouse and keyboard
that is detected. If a flawed detection software messes up recognizing your hardware, you could install, and reboot to a frozen mousepointer, or a 640 x 480 screen on your new 24" monitor. The xorg files in some distributions no longer provide useful info like lists of available screenmodes and resolutions, replaced by a line that reads 'detected monitor'. If you download a couple dozen varied examples people have posted over the years, print them, and compare them, you can usually make your own, filled in with the correct info about your hardware, comparable to filling out a 1040 EZ on april 15th :)

---

