---
title: "Rosegarden composition to .wav"
date: 2010-06-15
forum: Ubuntu Studio
---

### Post by Anaphylaxis on 2010-06-15
Hi! 

I want to create a .wav file from what I have composed in the notation editor in Rosegarden, using zynaddsubFX as midi output. 

Rosegarden's official tutorial is talking about using Kmix, but I am on Gnome, and seriously, it is awfully confusing for a n00b. 

I managed to direct output to ardour, and record from ardour. Is there another way to produce a .wav file/export my creations from rosegarden? :-k

---

### Post by Pablo_F on 2010-06-17
> Rosegarden's official tutorial is talking about using Kmix, but I am on Gnome, and seriously, it is awfully confusing for a n00b. 

afaik, kamix is an alsa mixer for KDE. You can use gamix, qamix, gnome-alsamixer or plain alsamixer (CLI) instead. All of these programs are "alsa mixers" and do the same thing (accessing the internal levels, mixers, etc, of your card).  If your card is "commercial" you need one of the above. Depending on the audio card, other utilities are recommended: envy24control for ice1712 cards, for example. 

Using ardour is a good idea but if you want it very simple, you can use jack_capture or timemachine, for example (simple audio recorders for jack).
Also, you may want to check this thread, in case you have troubles with zynaddsubfx.
  [http://ubuntuforums.org/showthread.php?t=1491496](http://ubuntuforums.org/showthread.php?t=1491496)

Cheers! Pablo

---

### Post by zettberlin on 2010-06-18
If only Zynadd is involved, you may want to try the recording-function of Zynadd itself.
Always choose the "Advanced" Frontend of Zynadd, never touch the stupid "Beginner"-Mode - you need all the possibilities in the real GUI to get the best out of Zyn. In the Main Window of Zynadd you find the entry "Record" in the Menu. Once you have chosen a name for a WAV-File you can start the recording using the controls in the upper middle of Zynadd and after that your tune in Rosegarden.

---

### Post by pdxken on 2010-06-18
Rosegarden will also record audio from Zynaddsubfx or any other soft synth if you connect the synth audio back into Rosegarden through jack connect.

Rosegardenmusic.com has a tutorial that explains how as I recall.

Hmm. Maybe it's in the Doc section.
[http://www.rosegardenmusic.com/doc/en/studio-audio-routing.html](http://www.rosegardenmusic.com/doc/en/studio-audio-routing.html)
 Ken.

---

