---
title: "M-Audio KeyStudio"
date: 2010-03-05
forum: Ubuntu Studio
---

### Post by zachws on 2010-03-05
Would like to use the M-audio Keystudio 49 with Koala.

lsusb recognizes it, but not audacity or ardour.

All I'm trying to do is have recording capability and monitoring.

Thanks!

---

### Post by Capoeira on 2010-03-05
it's not ardour or audacity wich will recognize it....look in the "alsa"-tab in qjackctl and than conect to ardour or to a instrument

---

### Post by Tahakki on 2010-03-06
Here's what I did to get a USB keyboard going:

1. Install JACK and JACK Control.
2. Install ZynAddSubFX (a softsynth) and Ardour. (These are all in the repos).
3. Plug in your keyboard and start Jack Control.
4. Open the connections screen and connect 'USB Midi' to 'Zynaddsubfx'.
5. Check it's working in Zyn, then connect Zyn to Ardour. You should be able to record now. :)

---

