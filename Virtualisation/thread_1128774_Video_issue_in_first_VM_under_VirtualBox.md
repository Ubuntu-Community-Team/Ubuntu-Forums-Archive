---
title: "Video issue in first VM under VirtualBox"
date: 2009-04-17
forum: Virtualisation
---

### Post by Bapu on 2009-04-17
Each time I boot the VM I'm told that there is a new Display device requiring a driver. When I tell the Wizard to search the driver CD for my video card (NVIDIA Geforece 8600 GT) I'm told there is no driver for the device.

The max display I can get in the VM is 800x600 16 colors. Is the best I can expect?

Ubuntu located the driver for the video card and I have 1680 x 1050 screen resolution on the Ubuntu desktop.

Any help would be appreciated.

---

### Post by RedSingularity on 2009-04-18
You need to enable/install the "Vbox Guest additions" in order to have a good full screen resolution.

---

### Post by Bapu on 2009-04-18
Thanks, that worked.

My next VM is an Exchange Server with a c: drive and a d: drive. How will I load them into the my second VM using Ghost images?

When I created my secon VM it only asks to create the Boot drive. How dd I create a secondary drive in the VM to restore the D: drive from Ghost?

TIA for any help.

---

### Post by Bapu on 2009-04-19
As stated in another thread. I fugured this out. Just added two drives. DUH!

---

