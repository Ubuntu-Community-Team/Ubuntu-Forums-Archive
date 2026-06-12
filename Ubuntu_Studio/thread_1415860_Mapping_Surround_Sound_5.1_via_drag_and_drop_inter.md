---
title: "Mapping Surround Sound 5.1 via drag and drop interface"
date: 2010-02-25
forum: Ubuntu Studio
---

### Post by lexen on 2010-02-25
Hello.  I am in a band and we are recording an album at a recording studio.  I had, for example, 7 mics on the drums.  I would like to find a way to map these tracks to 5.1 surround sound.  Audacity can do this manually, where I set the recorded track to a specific track on the audio file, but I cannot find a way to set a track to a position between the tracks, by means of adjusting percentages between tracks.

   I know that's a lot to ask, but I was just wondering if anyone knew of a program that currently does that.


Thank you,
Lexen

---

### Post by Stochastic on 2010-02-25
Ardour can do this.  It can be done with the internal panning system, or by adding a couple ambiphonic plugins (mono to b-format, followed by b-format to 5.1) to each channel (you'll need an ardour session with 5 or 6 output channels).  The benefit of the ambiphonic plugin route is that the panning can be automated, oh, and it sounds very spatially natural/realistic.

---

### Post by Redsandro on 2010-03-08
I want to do something similar, but Ardour keeps giving me stereo sound. The only System connections are playback_1 and playback_2.

However, I do have a SB Live! card and playing movies with surround sound in VLC Media Player works just fine.

How do I get those other channels in Ardour/Jack?

---

### Post by Stochastic on 2010-03-08
> **Redsandro said:**
> I want to do something similar, but Ardour keeps giving me stereo sound. The only System connections are playback_1 and playback_2.

However, I do have a SB Live! card and playing movies with surround sound in VLC Media Player works just fine.

How do I get those other channels in Ardour/Jack?

Sounds like you need to start jack with different channel parameters (if it's jack that only has two soundcard outs).  Unless of course you mean that Ardour is only giving two output channels.  Check the settings in qjackctl.

You may want to start your own thread though if that doesn't solve your problem.

---

### Post by Redsandro on 2010-03-09
Ah I didn't know. I just started **Ardour**, assuming it will do things that need to be done on it's own.

But I cannot set channels from **(default)** to **6**.
```
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: cannot set channel count to 6 for playback
ALSA: cannot configure playback channel
```
[SIZE="1"]5, 4 and 3 channels also do not work.[/SIZE]

Is it just me or is it a a bit weird that something most apps do for you needs to be done manually? Ignoring the fact that it didn't work by default for a moment, computers don't make mistakes but I do. ;)


Not sure if I'd need to start a new topic for this. It's sort of totally related. TS's question is answered, but if it was my question, then this would be my next step.

---

