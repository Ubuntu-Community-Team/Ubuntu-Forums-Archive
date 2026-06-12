---
title: "No sound when using JACK keyboard, Virtual MIDI Keyboard, etc"
date: 2015-06-10
forum: Ubuntu Studio
---

### Post by Daniel_Strickland on 2015-06-10
The title basically explains the issue. QJackCTL and jackd work fine, no problems there. My sound also works fine when running jack. The only problem is, the applications won't make sound when using them (IE: JACK Keyboard, Virtual MIDI Keyboard, et cetera)... Must be a settings issue within QJackCTL, possibly? 

By the way, I use Ubuntu 14.04.2 LTS, I've installed 'ubuntustudio-audio' metapackage, and I run AMD64. Yes, my sound card works fine. Everything seems to be configured correctly, except for my audio applications?

Any help would be greatly appreciated. :-)

---

### Post by jejeman on 2015-06-11
Those applications do not generate audio, only MIDI messages.
If a JACK client does not have Audio ports then it does not make sound.

---

### Post by Bucky Ball on 2015-06-11
Yep, you need to plug the keyboard 'virtually' into a sound generating synth. There should be two or three available and a drum machine from memory.

Launch and start Jack, launch a keyboard, launch a synth (haven't used the UStudio box in a while so don't remember the specific names), launch the Jack patching GUI (Setup?) and you will see the keyboard and syth there. Plug the ins and outs correctly, if they aren't already. Tweak around with your virtual connection cables until you get sound.

---

### Post by Daniel_Strickland on 2015-06-11
> **Bucky Ball said:**
> Yep, you need to plug the keyboard 'virtually' into a sound generating synth. There should be two or three available and a drum machine from memory.

Launch and start Jack, launch a keyboard, launch a synth (haven't used the UStudio box in a while so don't remember the specific names), launch the Jack patching GUI (Setup?) and you will see the keyboard and syth there. Plug the ins and outs correctly, if they aren't already. Tweak around with your virtual connection cables until you get sound.

Thank you SO much. That was the answer I've been looking for. I'm quite new to this, so please excuse my ignorance. You have literally done more to help then most people would on IRC Channels. I'll try it out! :-)

---

### Post by Bucky Ball on 2015-06-11
All good. Let's hope it works. Experiment and let us know how you go ...

Haven't used the UStudio box in awhile so that is from memory, but pretty close. You definitely need to virtually plug the virtual keyboard into a virtual synth (or an external sound generator via MIDI and back to the computer or another MIDI device but that comes later). ;)

The virtual keyboard in and of itself can't generate sound, as mentioned previously.

PS: You may discover some quirk where you have to launch the keyboard before the synth or vice versa. Roll with it ...

---

