---
title: "Help on connecting 2+ midi devices"
date: 2008-07-01
forum: Ubuntu Studio
---

### Post by secondstage on 2008-07-01
I have a keyboard (Some Yahama keyboard) that has midi in,out, and thru. I will be getting a synthesizer (Alesis Micron) that has the same interfaces and analog interfaces as well. Can I have to new synthesizer 'synthesize' the input from the first keyboard, and be able to take the synthesizer input and synthesize it? Do I just have a midi cable connect the two, and have the synthesizer analog out to an amp?

Thanks in advance.

--secondstage

---

### Post by secondstage on 2008-07-03
Nothing?

---

### Post by Stochastic on 2008-07-03
honestly I'm quite lost with your phrase > Can I have to new synthesizer 'synthesize' the input from the first keyboard, and be able to take the synthesizer input and synthesize it?  A MIDI signal is mostly just note-on note-off messages sent from a controller to a slave.  Try using terms like controller keyboard (or synth1) and slave keyboard (or synth2) to clarify your question.

---

### Post by secondstage on 2008-07-04
I'll try to clarify. I'm trying to have synth1 send a MIDI signal to synth2, so that synth2 can synthesize it. It would look like this
|synth1|-------|synth2|-----------|speakers|
.........^midi^........^audio out^

--secondstage

---

### Post by Stochastic on 2008-07-04
That's the entire point of MIDI, you merely need to connect a MIDI cable from the out of Synth1 to the In of Synth2.  One of my synths (korg X5) requires me to "Turn Local Off" before it will send MIDI out, so if you run into troubles, take a read through your manuals.

---

### Post by secondstage on 2008-07-04
Awesome. I have another question though. When I use JACK, and Hydrogen, or Jack, and Zynaddsubfx, the output sound like it is coming from a blown speaker. I checked the output with a set of headphones, and it sounds that same. Do you know what could be happening? I have Realtime, and monitor checked, Frames/Period is 1024, Sample rate + 44100, Period/Buffer = 2. I've have tried to change these values, but it come up with an error saying that JACK can't start.

---

