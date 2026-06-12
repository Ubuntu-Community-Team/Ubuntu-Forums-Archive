---
title: "Any help with upgrading GUI for mma (Linuxband/Lemma, alternate to Band In A Box)"
date: 2013-09-10
forum: The Cafe
---

### Post by su:bhatta on 2013-09-10
Hi, I have a strange request.

I am using mma for my accompaniments with either Linuxband or Lemma ( [http://linuxband.org/]("http://www.linuxband.org") OR [http://welltemperedstudio.wordpress.com/code/lemma/](http://welltemperedstudio.wordpress.com/code/lemma/))
Both  are nice GUI's for the MMA(Musical Midi Accompaniment) found here: [http://www.mellowood.ca/mma/](http://www.mellowood.ca/mma/)

Now both are pretty old but very much working but have certain limitations.

For Linuxband, it is the number of dependencies (although not many, 6-7). But the main problem is it uses the libjack-dev files a s dependancy.
In most distros now jackd2 comes by default, which has to be replaced with libjack-dev(which is difficult to use with pulseaudio-sink)

For Lemma, it has only 1 dependency (python-tk) but it doesn't give a midi-output port(I don't know how else to put it). 
In the program itself you have to choose a midi-engine(sound generator) e.g. Qsynth or Pygame which generates the sounds.

It would be great to tweak Linuxband to use jackd2 or for lemma to have a midi-out port which can be easily connected to Qsynth via Patchage.

I am not a programmer and I am requesting if any programmer with some interest in music (and some time to spare)to come ahead and look into the two apps (Linuxband/Lemma), and if it is easy for any tweaks to be made, to do it.

Any help is appreciated.

---

