---
title: "updating the bios thru a guest xp system?"
date: 2009-01-10
forum: Virtualisation
---

### Post by lime4x4 on 2009-01-10
Is it possible to update the motherboard bios thru a guest operating system?

---

### Post by Dedoimedo on 2009-01-11
Hello,

Unlikely. And definitely NOT recommended. Flashing bios is a tricky one anyhow. You certainly don't want a hypervisor in the middle guessing what needs to be done.

Never tried this; my warmest suggestion: don't.

Dedoimedo

---

### Post by thomasr on 2009-01-11
No, it is not - the bios you would be trying to update is a virtual bios, not the physical one. If you need to update the bios, most hav a self booting dos disk to do it with.

---

### Post by lime4x4 on 2009-01-11
That's what i thought. When i built the pc i never installed a floppy drive in it. Did find out thou that my motherboard bios can be updated thru a usb stick

---

### Post by HotShotDJ on 2009-01-11
> **lime4x4 said:**
> That's what i thought. When i built the pc i never installed a floppy drive in it. Did find out thou that my motherboard bios can be updated thru a usb stickYou can also flash your BIOS using a bootable CD (see: [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html) ).  YAO (Yet Another Option).

---

