---
title: "overdrive soundcard"
date: 2008-05-18
forum: Ubuntu Studio
---

### Post by cpicon92 on 2008-05-18
Hi, i have a ThinkPad r61, and the speakers really aren't very loud. In VLC i can set the volume up over 100 and really loud, ok sounding, audio. Is there anyway I can push the maximum alsa volume any higher? Or any program that would allow me to make the audio louder?

---

### Post by Stochastic on 2008-05-19
Not really.  Though software gain is allways possible, you'll just be clipping the sound once it reaches your soundcard.  If you really want to try this out start JACK, start Jack Rack (have the LADSPA plugins installed), and add some gain effects to your sound (if you're using VLC you'll need to set JACK as your Audio Output Module in the Preferences).  This is an excessive chain of software if all you want to do is play an audio file.

You can also check all your alsa levels in alsamixer if you install it first - it's quite possible your "quiet speakers" are actually because of a particular output channel being turned down.

Your other option is to add gain after your soundcard's D/A conversion.  You'll need an analog amplifier to do this, which means some internal re-wiring (don't do this if you don't have experience opening computers!!! you'll break things!!!) and that's assuming the speakers could handle any more power.  A local electronics boutique may be your best bet for a mod of this nature.

Probably your alsa levels are down too low.

---

### Post by cpicon92 on 2008-06-21
thanks, this was a big help

---

