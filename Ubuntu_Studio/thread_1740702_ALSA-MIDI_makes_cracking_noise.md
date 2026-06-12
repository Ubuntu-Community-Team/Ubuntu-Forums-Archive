---
title: "ALSA-MIDI makes cracking noise"
date: 2011-04-27
forum: Ubuntu Studio
---

### Post by Troubadix-der-Barde on 2011-04-27
Hello,

I´m starting with Ubuntu Studio and am very happy how well everthing works. But of course still got some problems.

My biggest at the moment: I get a strange cracking noise, if I use ALSA-MIDI. It sounds as if the midi information becomes audio. So it happens just if a new MIDI-information comes (start note, end note, etc).

There are no xruns in that moments.

In Jack-MIDI everything ist good. If I connect all just in Jack-MIDI there are no problems.

System: Ubuntu Studio (Maverick Meerkat), Vaio (i7), Edirol FA-101

Anybody got an idea?


Thanks and greets.




Edith: Forgot to say: My favorite MIDI-Sequenzer at the moment ist MusE. And MusE doesn´t appear in Jack-MIDI (neither with the help of a2jmidid). So at the moment I´m not able to use just Jack-MIDI. Rosegarden appears, but runs very unstable itself, so I would prefer MusE.

---

### Post by Troubadix-der-Barde on 2011-04-29
Ok, the Alsa-Midi still makes the crackling noise, but I solved my problem. In the default repository of Ubuntu-Studio just MusE 1.0.1 is available. And in MusE 1.0.1 there is no Jack-Midi. In the newer version (MusE 1.1) Jack-Midi is supported. Now I don´t need to use ALSA-MIDI (and at the moment that makes me very happy :D)

Maybe it would not be the worst thing to update MusE in Ubuntu Studio, as for me it seems to be a very stable sequencer. Soon they will release MusE 2.

Thanks to the community.

---

