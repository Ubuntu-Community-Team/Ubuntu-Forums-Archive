---
title: "Plugged in a USB-to-MIDI cable and got this error"
date: 2011-12-08
forum: Ubuntu Studio
---

### Post by isync on 2011-12-08
```
Dec  9 01:24:19 lenovo kernel: [  358.746342] usb 2-1.3: new full speed USB device number 5 using ehci_hcd
Dec  9 01:24:19 lenovo mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3"
Dec  9 01:24:19 lenovo mtp-probe: bus: 2, device: 5 was not an MTP device
Dec  9 01:24:19 lenovo pulseaudio[2140]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Dec  9 01:24:19 lenovo pulseaudio[2140]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="usb-MIDITECH_MIDILINK-mini_MIDITECH-FE-1A00-07DB0311-MIDILINK-mini-00-MIDILINKmini" card_name="alsa_card.usb-MIDITECH_MIDILINK-mini_MIDITECH-FE-1A00-07DB0311-MIDILINK-mini-00-MIDILINKmini" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
```

Is this a problem with the device (not usable under Linux?) or a problem with my system?

uname -a: Linux laptop Lenovo U160 3.0.0-13-generic-pae #22-Ubuntu SMP Wed Nov 2 15:17:35 UTC 2011 i686 i686 i386 GNU/Linux
This is a multiple times dist-upgraded system, btw.

---

### Post by isync on 2011-12-11
No one using a similar cable? No music making on Linux?? OT?

---

