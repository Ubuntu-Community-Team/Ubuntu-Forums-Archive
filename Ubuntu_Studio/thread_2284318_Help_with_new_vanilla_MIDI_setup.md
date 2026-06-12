---
title: "Help with new vanilla MIDI setup"
date: 2015-06-28
forum: Ubuntu Studio
---

### Post by selvaswami2 on 2015-06-28
I've got an Axiom 61 MIDI keyboard connected via USB to my gaming computer, and just wiped it to put a brand new Ubuntu Studio 14.04 installation on it.

No sound, and not entirely sure how to proceed.

All I wish to do for now is get the keyboard playing. I'll get into recording and composing later.

What are a newbie's first steps?

I found libremusicproduction.com and it has a solid tutorial on JACK, but I am hopeful someone experienced can get me playing my keyboard for now while I learn.

Thanks,

Selvaswami

---

### Post by jejeman on 2015-06-29
No sound? When?
You have general sound, no?

You of course know that MIDI is not sound. You need a sound module to make sound from MIDI data.

---

### Post by selvaswami2 on 2015-06-29
No sound through the computer speakers or headphones. I've tried various apps like Rosegarden, Hydrogen, Audacity and the screen registers any notes I play on the piano keyboard, but no sound.

---

### Post by jejeman on 2015-06-30
Still, it is not clear. Do you have sound when you play some audio file?

---

### Post by selvaswami2 on 2015-07-04
No sound at any time by any means from the Axiom-61 controller/keyboard. Yet I can play anything off the hard drive or YouTube. It's not the computer or speakers or headphones. The Axiom-61 worked fine on Windows OS in the music store. they don't know anything about Ubuntu, so no help there.

I've settled on Audacity as my software, and playing the keyboard registers on the screen, but I'd kinda like to hear what I play as well.

---

### Post by jejeman on 2015-07-04
As fas as I can see this Axiom is just a MIDI controller, it is not a synth. There are no audio outputs, so it does not generate sound, at least not an analog one. So, this Axiom on its own does not make sound, just MIDI data.
Now, I don't know what they have implemented on the USB side. Just MIDI or audio as well? Is it recognised as both MIDI device and audio device?
Give
```
aplay -l
amidi -l
```Copy this outputs here so I can give you an advice.

---

### Post by yoshii on 2015-08-23
You need to first try and install the drivers for the Axiom.  Since this is linux instead of windows, wine will be involved and the process may or may not work. However, there is a slim chance that the Axiom is USB Class Compliant, meaning that driver installation isn't necessary.  Please consult the M-Audio support website to find out which it is, and if there are linux or windows drivers available.  Hopefully it will work out, but there's a chance that it won't.  If so, you may have to find a different hardware MIDI controller that is USB Class Compliant, such as the Q25 or Q49 by Alesis.

---

### Post by MartyBuntu on 2015-08-23
Here's a good guide:

[http://terokarvinen.com/2014/usb-midi-keyboard-on-linux-akai-lpk25-professional](http://terokarvinen.com/2014/usb-midi-keyboard-on-linux-akai-lpk25-professional)

---

### Post by yoshii on 2015-09-13
If the Axiom is already showing up as MIDI activity when you play notes in some Linux DAWs, then I don't think you need to install drivers for the Axiom.  But you will need to set up a virtual instrument for the Axiom to trigger before you get any sound.  The Axiom is just a MIDI trigger device.  It is used to transmit note on/off triggers and the like.  It's not a synthesizer.  VST instruments would work in Reaper with wine but like any DAW it takes setting up the settings/preferences and loading up some virtual instruments.  Linux has it's own types off virtual instruments.  There are freeware ones you can download just like freeware VST instruments.  Ubuntu Studio comes with some of the free Linux ones.

---

