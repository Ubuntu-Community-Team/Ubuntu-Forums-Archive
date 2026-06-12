---
title: "Voice chat in EVE Online?"
date: 2009-07-05
forum: Wine
---

### Post by X-BANE on 2009-07-05
Is it actually possible to get voice chat working CLEARLY? I can sort of get it to work if I set ALSA with driver emulation in the Wine audio tab, but whenever I try to speak I deafen the other person with static! :lolflag:

Is there anyway of getting nice, clean & static free voice chat?

---

### Post by ltrinh on 2009-08-11
I just tested it out with wine 1.1.27 and it works fine.  Make sure you test your mic out with sound recorder to make sure it works in ubuntu first.  You could also test it out in skype if you prefer. After that, try it out in wine by performing an echo test.  If your mic doesn't record your voice but you can hear yourself through your speakers then do the following:

1: Install Gnome Asla-mixer
2: Run Gnome Alsa-mixer under sound and video in applications
3: Make sure the capture slider on the far right is all the way up
4: Make sure that the rec check box at the bottom of capture is checked.


That should be it.  It's what worked for me anyways.  Hope this helps.

---

