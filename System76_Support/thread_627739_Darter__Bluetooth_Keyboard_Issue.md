---
title: "Darter / Bluetooth Keyboard Issue"
date: 2007-11-30
forum: System76 Support
---

### Post by agisfox on 2007-11-30
I've been having a issue with an Apple Wireless Keyboard I'm trying to use with the Darter.

When trying to connect I get the error message
"Can't create HID control channel: Connection timed out"
HIDD is enabled, and my options in /etc/default/bluetooth and /etc/bluetooth/hcid.conf should be good.  They and the output of hcidump from a search/connection attempt are attached.

---

### Post by thomasaaron on 2007-11-30
Try this:
[http://filer.case.edu/jec24/2007/11/apple-wireless-keyboard-setup-ubuntu.html](http://filer.case.edu/jec24/2007/11/apple-wireless-keyboard-setup-ubuntu.html)
or this
[http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673)

---

### Post by agisfox on 2007-11-30
Thanks; that fixed it, the PIN # part was what I was missing.
(For some reason my searches hadn't turned those up).

---

