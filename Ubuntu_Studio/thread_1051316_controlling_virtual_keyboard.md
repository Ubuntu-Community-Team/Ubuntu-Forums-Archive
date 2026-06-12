---
title: "controlling virtual keyboard"
date: 2009-01-26
forum: Ubuntu Studio
---

### Post by davesollows on 2009-01-26
Hi,

Can anyone clue me in as to how I am supposed to control the Virtual Keyboard with my KORG microKontrol.  I tried the following connections in Jack:

microKontrol 0: > midithru0 > Virtual Keyboard0 > Qsynth0 > system out 0

but i can not get teh microKontrol to trigger Virtual Keyboard.

Any help on the matter is greatly appreciated.

---

### Post by thorgal on 2009-01-26
your korg does have a MIDI output, does it ?
it should show up in the ALSA tab of qjackctl as a port in the left hand side window. Connect it to the Qsynth MIDI port in the right hand side window (MIDI capture). I don't understand why you want it to go through a virtual keyboard.

---

### Post by davesollows on 2009-01-26
Thank I managed to get it working...when I tried that method before i was using id:0, as it turns out id 1 on the microkontrol corresponds to the usb.  it is working now as KORG microKontrol > qsynth in jack. thanks so much!

---

