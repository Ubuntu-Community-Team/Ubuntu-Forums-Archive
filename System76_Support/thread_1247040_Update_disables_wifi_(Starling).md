---
title: "Update disables wifi (Starling)"
date: 2009-08-22
forum: System76 Support
---

### Post by RichardK on 2009-08-22
Performed the regular update last night (using wifi), and reinstalled the System76 driver. Upon reboot, wifi was disabled.

Tried bringing wlan1 up manually, but there was no wireless module installed.

Finally was able to fix this by editing /etc/modprobe.d/rtl8187.conf
and commenting out "blacklist rtl8187"

I ran the System76 driver update again and confirmed that it was blacklisting the rtl8187 module.  Why is it doing this?  Is the rtl8187 the correct driver to use?

Thanks,
Richard

---

### Post by thomasaaron on 2009-08-24
rtl8187 is not the correct driver to use. It has a really bad range issue. The System76 driver is compiling a different driver for your wireless - r8187.

So, run the driver again and reboot your machine. Is your wireless LED on. (I'm betting it is not.) If I'm correct do this...

1. On the leading, right edge of your Starling there is a springloaded wireless toggle switch. Press it *ONE* time to the right.

2. Reboot your computer.

Now, your wireless LED should be on, and you should be able to connect with much better range.

---

### Post by RichardK on 2009-08-25
Worked. Thanks.  It's a bit counterintuitive. Pressing the switch doesn't have any visible effect except make the hard drive light come on. It must have done something, though, because after the reboot, the wireless LED is on and wireless is enabled.

---

