---
title: "Daru2, Gusty, no sound through headphone jack"
date: 2007-10-30
forum: System76 Support
---

### Post by GregCwx1 on 2007-10-30
I believe other's have had this problem and hopefully it's an easy fix.

I'm running gusty on the daru2 and sound works fine through the tiny laptop speakers. However, I'm not getting any output from the headphone jack.

Here's an error about ALSA showing up in dmesg:

[   16.416000] ALSA /opt/system76/system76-driver/src/sys76-alsa-1.0.14/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:558: hda_intel: azx_get_response timeout, switching to polling mode...
[   16.576000] ALSA /opt/system76/system76-driver/src/sys76-alsa-1.0.14/pci/hda/../../alsa-kernel/pci/hda/patch_si3054.c:244: si3054: cannot initialize. EXT MID = 0000

Here's the output from:
>cat /etc/modprobe.d/alsa-base | tail -5:

options snd-hda-intel model=targa-dig
options snd-hda-intel model=targa-dig
options snd-hda-intel model=targa-dig
options snd-hda-intel model=targa-dig
options snd-hda-intel model=targa-dig

Any help would be greatly appreciated. Thanks!

(Oh, while I'm here, any progress on the higher resolution laptop screen I thought I had under Feisty?)

-Greg

---

### Post by thomasaaron on 2007-10-31
Double-click the speaker icon. In the resulting window go to Edit > Prefs. Make sure ALL boxes are checked.

Now you should have a bunch more controls in your Sound Controls. I think that under "Switches" there is a little box that needs to be checked for headphones.

Also, make sure they are not muted under any of the other tabs.

---

### Post by GregCwx1 on 2007-10-31
Thanks Thomas!

I had to double-click the panel icon, go to the "switches" tab and click headphone on. That was too easy.

---

