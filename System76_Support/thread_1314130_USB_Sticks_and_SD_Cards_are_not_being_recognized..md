---
title: "USB Sticks and SD Cards are not being recognized."
date: 2009-11-04
forum: System76 Support
---

### Post by xakh on 2009-11-04
I'm overall having a fairly smooth transition to Karmic, but right now no USB sticks or SD cards I plug into my panp4 are recognized. Has anyone else had this problem?

---

### Post by thomasaaron on 2009-11-04
I'm seeing some USB port problems after the online upgrade, but none so far after fresh installs.

I've not figured out what is going on yet. I'm working with another customer on resolving this, albeit on a different computer. But I'll report back with my findings.

---

### Post by abulluck on 2009-11-04
I have the same issue on a PanP4.  Haven't checked and SD card, but a kingston I plugged in last night would not recognize.  Had to manually mount it.

Would love a workaround here.

---

### Post by gpstar on 2009-11-04
there's a bug, seems to be floating around on the 64bit installs.

a temp fix is run this in the terminal

sudo udev stop
sudo udev start

then esata/usb/sd card reader will automount after.

---

### Post by gpstar on 2009-11-04
I see there's a update in the proposed updates for karmic that you can get in the update manager now for udev which fixes the problem of detection/automounting of hotswap devices now.

---

