---
title: "using  qsynth and jack. ubuntu noob needs help."
date: 2009-04-22
forum: Ubuntu Studio
---

### Post by khayden39005 on 2009-04-22
i dont know if its just different vocabulary or what but im having a hard time getting anything too work. im not new to daw concepts but i am brand new to ubuntu.
jack completely stumps me. i think i get the idea i just cant make it work.
i open jack and start it. open qsynth and load a sound font. how do i use jack to connect my midicontrol keyboard to qsynth. i picture this whole process to be something like propellorheads reason with its virtual patch cables. am i completely wrong? ive read thru many tuts and im stil missing something. any help is sincerely appreciated.
btw. im running ubuntu 8.10. it seems like everything is working all drivers are there. my midi controller shows up. im just daft.

---

### Post by eye208 on 2009-04-23
> **khayden39005 said:**
> how do i use jack to connect my midicontrol keyboard to qsynth.
Click the "Connect" button.

[img]http://qjackctl.sourceforge.net/image/qjackctlMainForm1.png[/img]

On the "Audio" tab, connect the synthesizer to your soundcard output. On the "MIDI" or "ALSA" tab, connect your MIDI interface/keyboard to Qsynth. Now you should be able to play Qsynth live.

If you want to use a MIDI/audio sequencer, it's a little more complicated of course. You need a MIDI connection from the keyboard to the sequencer, and from the sequencer to Qsynth. And you need audio connections from Qsynth back to the sequencer and from the sequencer to the soundcard output.

[img]http://qjackctl.sourceforge.net/image/qjackctlConnectionsForm1.png[/img]

---

### Post by markbuntu on 2009-04-23
Get

patchage

It is a lot less confusing. Patchage shows everything in one big window and it is just point and click to connect stuff up.

---

