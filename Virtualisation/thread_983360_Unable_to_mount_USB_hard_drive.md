---
title: "Unable to mount USB hard drive"
date: 2008-11-15
forum: Virtualisation
---

### Post by techmba on 2008-11-15
I upgraded to 8.10 on a HP nw8440 laptop and now i have one issue with VMplayer 2.5 (with WinXP VM):


* USB drives are no longer getting mounted in WinXP. The behavior that is see is that the USB drive gets discovered and after a few seconds, the drive gets mounted back on the Ubuntu host. I searched the forums but did not see any posts. The usb config entries in the vmx file are:

usb.present = "TRUE"
usb.autoConnect.device0 = ""
usb.autoConnect.device1 = ""
usb.generic.autoconnect = "TRUE"
usb.generic.skipSetConfig = "TRUE"
usb.autoConnect.device2 = ""
usb.autoConnect.device3 = ""

This was working fine in Ubuntu 8.04 + VMplayer 2.0.5. Could you please recommend any trouble shooting steps ?

---

### Post by rimbaud on 2008-12-11
I am having the same problems and have posted questions on VmWare's forums, but no response so far.  There are lots of USB threads.

---

### Post by DanM718 on 2008-12-11
I had trouble using USB in VMWare.

Don't think I ever got it working tbh

Dan

---

