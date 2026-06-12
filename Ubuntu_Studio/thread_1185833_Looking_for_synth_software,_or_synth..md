---
title: "Looking for synth software, or synth."
date: 2009-06-12
forum: Ubuntu Studio
---

### Post by feardotcom on 2009-06-12
I'm the market for a usb keyboard, I'm thinking of a M-Audio Axiom 61, but from what I understand about it is it doesn't have all the fancy sounds and tones a synth does. I was curious is if someone could tell me if there was a program that let you change the tones coming from a keyboard in real time? Or could someone just point out a decent beginner-intermediate synth thats no to expensive.

---

### Post by kayosiii on 2009-06-13
The Axiom does not send sound at all. It sends midi  signals (instructions along the lines of start playing this note, stop playing this note)...

What you are looking for is software that can take the midi instruction to play a note and turn that into a sound (synthesis software). There is a rather exhaustive list at apps.

 [http://apps.linuxaudio.org/apps/categories/software_sound_synthesis_and_music_composition_packages](http://apps.linuxaudio.org/apps/categories/software_sound_synthesis_and_music_composition_packages)

ZynAddSubFX is a good place to start. It sounds reasonably good and is relatively easy to set up. Amsynth is also quite easy to use. 

If you are looking for replications of real intstruments QSynth works quite well if you have soundfonts, LinuxSampler works for Gig files and there is a comercial physical Piano synth (called pianoteq) that you could look into... .

Hopefully that will help you get started

---

### Post by JockVSJock on 2009-06-13
That is a pretty good list, here is another one: 

[http://linux-sound.org/](http://linux-sound.org/)

---

### Post by sgx on 2009-06-21
> **feardotcom said:**
> I'm the market for a usb keyboard, I'm thinking of a M-Audio Axiom 61, but from what I understand about it is it doesn't have all the fancy sounds and tones a synth does. I was curious is if someone could tell me if there was a program that let you change the tones coming from a keyboard in real time? Or could someone just point out a decent beginner-intermediate synth thats no to expensive.

A yamaha mm6/mm8 (61 or 88 keys) has usb and real midi ports, hundreds of great built-in sounds, layer any 2, add built-in fx, run drum patterns and arps, record 5 tracks, and record the output can to your soundcard line-in.
Then the midi out of the mm6 can trigger linux synths like zynaddsubfx, which is a worldclass synth, and when used with the rakarrack multi-fx app, is the match for most synth out there on any platform! It's a 16 part multi-timbral beast!
Cheers

---

