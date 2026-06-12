---
title: "Suggest An Application: Simple Audio Sample Player"
date: 2008-06-24
forum: Ubuntu Studio
---

### Post by studiesinsound on 2008-06-24
Hi,

I'm thinking there is probably an application in Ubuntu Studio (or 1 I can install) that does what I need as it is a fairly straightforward thing but I can't find it.

Here's what I would like to do:
Record all sorts of found sounds, environmental sounds, pretty much every thing with my portable hand held recorder.
Import the short wav files into Ubuntu (so far so good I can do all of this.)

Trigger the samples via midi.  Sort of like an MPC Style sampler.
I have an M-Aduio Trigger finger which works wonderfully with Ubuntu.

So is there a peice of software wherin I can have wav samples triggered via midi?    
Hopefully something where I can assign the midi notes to the specific samples?
I also would love if this dream application was jack compatible.

nothing crazy and fancy 
I thought "linuxsampler" was what I wanted but after reading up on that application that is more of an instrument sampler application, not an audio sample player.

Thanks for any input.

-John

---

### Post by thorgal on 2008-06-24
you can definitely use hydrogen, the drum sampler and sequencer (all in one) because the drumkits are actually easy to create and can be differente from drum sounds, it can be whatever wav samples you have around. 

or

linuxsampler (frontend qsampler) where you can create "instruments" using your own samples in the gig format (using gigedit).

I forgot to add that hydrogen can be triggered via MIDI and can record MIDI events.

---

### Post by studiesinsound on 2008-06-24
thank you thorgal.
Since I am already familiar with using hydrogen I will pursue learning how to create a kit.  I also like how hydrogen is velocity sensitive and also has some effects.

Good call.  Off to learn how to build a kit.

That's a good suggestion

linuxsampler looks great and I will certainly pursue that in the future.

---

### Post by thorgal on 2008-06-25
I would add that you should be careful with hydrogen drumkit. I suggest you encode your samples to FLAC although I don't remember if FLAC support is in version 0.9.3 or 0.9.4 only. I used to have a huge drumkit (former NS_Kit7 free) and hydrogen does not do disk streaming so it loads the whole thing into RAM ... you are warned ;)

---

### Post by studiesinsound on 2008-06-26
alright, I am going to go ahead and run with hydrogen on this one.
Can you recommend any good .wav to flac file converters?

---

### Post by Stochastic on 2008-06-26
try sound converter ```
sudo apt-get install soundconverter
```

---

