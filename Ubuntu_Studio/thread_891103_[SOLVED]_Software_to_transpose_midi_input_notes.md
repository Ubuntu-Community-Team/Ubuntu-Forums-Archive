---
title: "[SOLVED] Software to transpose midi input notes?"
date: 2008-08-15
forum: Ubuntu Studio
---

### Post by phil the dill on 2008-08-15
Hi,

My external midi keyboard has no facility to transpose the notes it sends to my computer (ie make them higher or lower). I want to use it to play a bass guitar track on my soundcard with a good soundfont I've got, but the lowest key on my keyboard isn't low enough to play the lowest note in the soundfont. I want the input notes to be lowered by an octave.

Is there some software that will take a midi input from my keyboard and transpose it so my soundcard receives a lower midi note?

I found QMidiRoute, which looks like it should be able to do what I want, but I can't get any output from it, and there's no manual so I've got no idea what to do next.

---

### Post by phil the dill on 2008-08-15
Ok I've just found out how to get QMidiRoute to work now - I found a post in this forum about QMidiArp, and I realised that QMidiArp and QMidiRoute follow the same configuration pattern. 

I loaded the QMidiArp example file 'demo_up_down.qma' that is located in /usr/share/qmidiarp, and I realised that the 'Event Input' section on a QMidiRoute map tab specified the range of input values that QMidiRoute would act on. QMidiArp has a default 'Note' range of 0 to 127, but QMidiRoute defaults to a note range of 0 - not very useful.

I had to change the default 'Note' range from 0:0 to 0:127 and then set the Note Offset value to -12. Now any note I play on my midi keyboard is transposed down by 12 semitones.

---

