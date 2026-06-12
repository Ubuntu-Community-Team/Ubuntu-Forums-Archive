---
title: "Ubuntu Studio, Rosegarden, MuseScore"
date: 2014-05-29
forum: Ubuntu Studio
---

### Post by Zaglamir on 2014-05-29
Hi all,

My current system is Ubuntu 14.04LTS. One of my hobbies is using MuseScore to compose music. However, it doesn't allow mixing in a dynamic fashion. My solution to this was to attempt to install Rosegarden to edit the velocity, etc on my MIDI files. However, I've never been able to get Rosegarden to output sound, despite trying JACK, FluidSynth, etc. 

It was suggested to me that my problem may lie in how JACK is supposed to connect things together and that not using the more open Ubuntu Studio kernel could be holding me back in this way. My question is: does this sound feasible? Is it likely that using Ubuntu-Vanilla could hinder JACKs ability to connect the MIDI output of rosegarden to the external speakers?

Also, to save multiple posts, this is also my work machine. If I were to upgrade to Ubuntu Studio, should I expect installed programs to act strangely? For instance, I use an analysis program called ROOT, which relies on a number of compiled libraries and whatnot. Will this be effected by an upgrade?

Cheers!
Zach

---

### Post by gboer01 on 2014-06-03
Did you load a sound font (SF2) in FluidSynth? If not: no sound. My Rosegarden works with and without JACK. Sound fonts are of type *.sf2, there may be one installed in /usr/share/sounds/sf2.
In Rosegarden go to Studio -> Manage Synth Plugins. Choose FluidSynth on track 1, Press Editor>> and load the sound font.
Cheers

---

