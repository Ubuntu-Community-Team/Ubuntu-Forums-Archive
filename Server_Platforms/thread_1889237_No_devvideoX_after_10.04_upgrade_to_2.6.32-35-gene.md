---
title: "No /dev/videoX after 10.04 upgrade to 2.6.32-35-generic-pae for EASYCAP DC60"
date: 2011-12-01
forum: Server Platforms
---

### Post by mnuser on 2011-12-01
All,

semi-Noob here, with the following issue:

I used easycap dc60 as an NTSC capture card for zoneminder - after upgrade to 2.6.32-35-generic-pae /dev/videoX no longer exists after device plugin.

**DMESG OUTPUT**
[  101.712054] usb 1-4: new high speed USB device using ehci_hcd and address 6
[  101.845084] usb 1-4: configuration #1 chosen from 1 choice

**LSUSB OUTPUT**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 002: ID 04d8:fc73 Microchip Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 006: ID 05e1:0408 Syntek Semiconductor Co., Ltd** 
Bus 001 Device 004: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by SteveDee on 2011-12-01
> **mnuser said:**
> ... /dev/videoX no longer exists after device plugin...

You might find the answer in this thread: [http://ubuntuforums.org/showthread.php?t=924504](http://ubuntuforums.org/showthread.php?t=924504)

---

### Post by mnuser on 2011-12-01
Thank you for your reply - I had reviewed that thread, but it looks like it trickled off to a still non-working state.  I have also not been able to find any reference to my issue in the change logs.  The older driver on source-forge for this device has also disappeared.  Is there an easy way I can go back to the older kernel that worked?

---

### Post by SteveDee on 2011-12-01
> **mnuser said:**
> ...is there an easy way I can go back to the older kernel that worked?

If you haven't deleted any of your earlier kernels, then just boot into Grub and select it from the list.

If you've cleaned-up by deleting older kernels, then just go to Synaptic and re-install it.

'buntu saves kernel files and related modules in a way that allows you select and boot by version.

---

### Post by mnuser on 2011-12-01
I unfortunately cleaned them.  Any other ideas?

---

### Post by mnuser on 2011-12-02
Found my old driver file downloaded some time ago.  Seems the DIST no longer has support for this device included.

---

