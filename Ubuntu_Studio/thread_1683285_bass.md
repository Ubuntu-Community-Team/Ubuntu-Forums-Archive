---
title: "bass"
date: 2011-02-07
forum: Ubuntu Studio
---

### Post by kree8or on 2011-02-07
Hi,
Is there a program that runs on ubuntustudio that will allow me to add a base track , preferably using TAB notation?

---

### Post by Pablo_F on 2011-02-07
Hi, 

In tuxguitar you can add a midi track in tab notation, for guitar or bass. In other sequencers, like Rosegarden, qtractor or muse you can write midi tracks in a matrix editor. In Rosegarden, musescore, denemo, nted and others, you can also write notation. Note that, in some cases, you need an external soft synth.

If you are going to use tuxguitar and, at the same time, some jack-aware program (for example, ardour), you will need tuxguitar-alsa to have an alsa-MIDI output that you can connect to an alsa-midi-input-jack-audio-output soft synth. For example, you could use qsynth with some bass soundfont loaded.

Cheers, Pablo

---

