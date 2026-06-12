---
title: "Need help with MIDI"
date: 2016-07-28
forum: Ubuntu Studio
---

### Post by chkneater on 2016-07-28
Hi, can anyone help me figure out MIDI?  I have an E-MUXboard25 that I'm using in a USB port and (ubuntu Studio 14.04 RT) the system automatically detects it and installed the driver by itself.  The problem I'm having is A) what software do I need for playing and recording and B) how do I manage the connections in jack?  I have had success with the virtual keyboard but I know nothing about sequencers and such so any help is much appreciated!

---

### Post by jejeman on 2016-07-28
A) Software for playing MIDI files, or for playing with keyboard?
B) If you use Qjackctl you have two tabs for MIDI connections. MIDI tab for JACK MIDI, and ALSA for ALSA MIDI. Hardware is registered in ALSA tab. Software ports can appear in both tabs. Those are two &#8222;realms&#8220; of MIDI. By default, one can not communicate with other. You need to bridge them. Two ways to do that: with a2jmidid or via JACK option.

MIDI sequencers: Seq24, Muse, Ardour3+, Qtractor and few more.

---

### Post by deanpeters2 on 2016-08-22
From what I can tell online, the E-MU XBoard 25 is a relatively straight-forward USB MIDI keyboard controller?

If that's the case, then perhaps the chain you're looking for is:

MIDI-Controller out -> Sequencer MIDI In -> Sequencer MIDI Out -> Synthesizer MIDI In ...

... and then Synthesizer Audio Out -> System Audio In?

---

