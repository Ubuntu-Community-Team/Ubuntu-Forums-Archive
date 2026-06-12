---
title: "How to get MIDI out back to the keyboard speakers?"
date: 2015-03-27
forum: Ubuntu Studio
---

### Post by undiavolarem on 2015-03-27
I've searched for several hours with no sucess: I'm familiar with Jack connections, but when it comes to mix Jack and MIDI, it gets complicated.

My aim is to get MIDI sound from a keyboard through a MIDI IN/OUT cable, transform the notes with a good soundfont (with Qsynth or other), and get the sound back to the keyboard speakers.

Briefly, I would like to play my old Yamaha Clavinova keyboard with a better MIDI sound than the one that the soundfonts installed in the keyboard can provide. I manage to get the sound transformed with Qsynth come out through the computer speakers, but I find no way to connect it back to the keyboard speakers, since Qsynth doesn't have a MIDI-out connection, only MIDI-in.

My only "success" so far has been to connect it this way, letting Qsynth apart:

Clavinova OUT -> MIDI through IN
MIDI through OUT -> Clavinova IN

Which already gives me a better sound than the keyboard's default one, but with no possibility to really choose a good sound font.

Any ideas about how to get this work?

---

### Post by jejeman on 2015-04-04
Looks to me you are trying something that is not possible. And your explanation is totally unclear.
First, there is no term as "MIDI sound". MIDI does not sound, it is just MIDI messages. MIDI transfers only MIDI data, not Audio data in any kind or form.

Here is what I understood.

So, your built in sounds in the hardware keyboard are bad, but qsynths are good, and you want them to be heard from the hardware keyboard speakers, not the computer speakers.
Okay. IF your hardware keyboard is a soundcard then it is possible. Choose your hardware keyboard as soundcard in jack.
IF not, than you are trying impossible.

---

