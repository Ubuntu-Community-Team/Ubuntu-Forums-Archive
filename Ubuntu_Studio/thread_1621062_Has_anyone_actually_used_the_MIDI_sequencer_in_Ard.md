---
title: "Has anyone actually used the MIDI sequencer in Ardour 3?"
date: 2010-11-13
forum: Ubuntu Studio
---

### Post by SleepWalkerX on 2010-11-13
I understand its in alpha, but has anyone played around with it?

I don't fully understand MIDI sequencing so I'm just trying to play around and see what I can do with it.  I understand a good bit, but I don't understand how a software synth like Hydrogen or AmSynth communicates with the midi sequencer (like in Ardour 3, for example).  

In patchage, I can't connect my USB Midi to ardour's midi input.  Perhaps I'm just confused as to how it works?

---

### Post by Pablo_F on 2010-11-13
Hi, 

> In patchage, I can't connect my USB Midi to ardour's midi input. Perhaps I'm just confused as to how it works? 

Ardour does not use alsa midi (green ports in patchage) but jack midi (red ports). You need the "alsa midi to jack midi daemon", this is, a2jmidid. Use the -e option to bridge the hardware ports, such as a midi keyboard.

I suggest you execute:

a2jmidid -e &

as the second script in the options tab of the setup of Jack Control.

Cheers! Pablo

---

### Post by SleepWalkerX on 2010-11-14
Cool Thanks!!!!

I can see ardour playing my midi notes.  But I'm still a little confused.  My synths, like Hydrogen, still show up as green ports.  How do I connect the synths to ardour?  This is all very new to me.

---

### Post by Pablo_F on 2010-11-14
If you run a2jmidid, you should see a box called "a2j" with all the alsa midi ports ported to jack midi (red ones) including hydrogen's. You can check in the Connection window of qjackctl aswell.

Patchage   <->  qjackctl

Blue   <->   Audio
Red    <->   MIDI (=jack midi)
Green  <->   ALSA (=alsa midi)

Anyway, check if your synths have a native jack midi option. Some have. If not, use the a2j ports for them too.

Cheers! Pablo

---

### Post by SleepWalkerX on 2010-11-14
Thanks again!  Yeah now I see them in a2j.  How should it look in patchage?  

a2j USB Midi <-> Ardour 3 Midi in

Ardour 3 Midi out <-> a2j Hydrogen Midi In
Ardour 3 Midi out <-> a2j AmSynth Midi In

Like that?  I'm not sure if I have this setup right.

---

### Post by Pablo_F on 2010-11-15
> a2j USB Midi <-> Ardour 3 Midi in

Ardour 3 Midi out <-> a2j Hydrogen Midi In
Ardour 3 Midi out <-> a2j AmSynth Midi In

Yes, that seems correct. But note that ardour has midi control ports as well. Make sure you are connecting to and from an ardour midi track (if you intend to do so).

Cheers! Pablo

---

### Post by SleepWalkerX on 2010-11-21
I only have one midi track in Ardour 3.  But that one track has 16 channels.  Is there a way to map each individual channel to a synthesizer?

edit:  I guess I'm still a little confused about this midi.  Should I make multiple midi tracks and map each of those to a synthesizer?

edit2:  Oh ok.  I think I got it.  I just mute each midi track until I need it.  Does this sound right?

---

