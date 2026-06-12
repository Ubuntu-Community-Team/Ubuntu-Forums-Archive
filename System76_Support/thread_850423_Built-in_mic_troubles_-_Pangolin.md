---
title: "Built-in mic troubles - Pangolin"
date: 2008-07-05
forum: System76 Support
---

### Post by matt5ash on 2008-07-05
Here's the trouble ... 

1)  The internal mic isn't sending sound signals anywhere ... no sound in the speakers, a set of clicks using the command arecord -vv -fdat foo.wav from the terminal.

2)  An external mic sends sound signals to the speakers, but also produces a set of clicks when using the arecord command.

I'm using a new Pangolin 64 that's about 1 week old.

Any help would be most welcome ... I really don't know how to proceed or what to do ...

thanks for any help

--matt

---

### Post by crichell on 2008-07-07
Hi Matt,

This is probably settings in volume control. Double click the speaker icon near the clock.

In Volume Control click Edit > Preferences and turn on each checkbox.

Turn up "Capture" on the Recording tab

On the Options tab you can choose between using your internal mic and an external mic. The Input Source option "Mic" is the plug in external mic and "Front Mic" is the internal microphones (around the LCD).

You can also adjust the Mic Boost sliders on the Playback tab to fine tune recording volume.

---

### Post by matt5ash on 2008-07-07
> **crichell said:**
> Hi Matt,

This is probably settings in volume control. Double click the speaker icon near the clock.

In Volume Control click Edit > Preferences and turn on each checkbox.

Turn up "Capture" on the Recording tab

On the Options tab you can choose between using your internal mic and an external mic. The Input Source option "Mic" is the plug in external mic and "Front Mic" is the internal microphones (around the LCD).

You can also adjust the Mic Boost sliders on the Playback tab to fine tune recording volume.

Hi crichell ...

Good idea but nope, that doesn't help ... Thanks very much for responding :-)  Maybe the details below will point to another helpful thought ...

details ...
There are two stereo sliders on the recording tab on this computer, One is Capture, the other is Digital.  The Capture slider is all the way up, and not muted, the Digital slider is all the way down and is muted.  So the mic doesn't work (yet)... (all the playback sliders are fully on and un-muted).  I tried playing with the Digital slider, it doesn't seem to do anything ... I really don't know what it's suppose to do though ... 

other notes ...
The little Sound Recorder app doesn't work for the internal or the external mics ... this might be another part of the problem ??

Something is working though ... with all the sliders full on there's a little bit of noise in the speakers, although no other sounds that I can hear.

Playback from an mp3 file works just fine ...

Hopefully, you'll have another good idea ...

thanks very much

--matt

---

### Post by thomasaaron on 2008-07-08
Hi, Matt.

Here are some screenshots to get the internal mic working on the Pangolin. Notice the settings on Sound Recorder as well.

---

### Post by thomasaaron on 2008-07-08
See this screenshot for getting an external mic working. Everything else is the same as above. 

NOTE: You are not going to get great sound with the internal mic. At first we thought it was due to ALSA, but it isn't that great with Windows either.

For the best quality, use an external mic. A USB headphone/mic set is also a great way to get high quality recording.

---

### Post by matt5ash on 2008-07-08
> **thomasaaron said:**
> See this screenshot for getting an external mic working. Everything else is the same as above. 

NOTE: You are not going to get great sound with the internal mic. At first we thought it was due to ALSA, but it isn't that great with Windows either.

For the best quality, use an external mic. A USB headphone/mic set is also a great way to get high quality recording.



Hi thomasaaron ...

Good news ... the internal mic (which always was working :-) is now set to actually record sounds.

Two Questions ...
So ... maybe I sorta understand ... there are three sliders in the mic pathway, Capture, Digital, Mic Boost (well, I used Front Mic for the  build-in mics).  If I turn a slider too high, some sort of feedback happens, and I get those clicking sounds ... Do I have the idea more or less correct ??

Last year I bought a Pangolin Value ... does that computer have a somewhat different mic setup ??  (Don't recall having as much trouble setting the sliders correctly).
thanks ...

In any event ... thank you very much for your help ... sending the pictures really was a great way to help me understand !!

Hope you folks enjoy the summer ...

--matt

---

### Post by thomasaaron on 2008-07-08
Yeah, I get the clicking sounds too. I don't fully understand all of the settings. I'm not sure that ALSA (which provides the sound support for Ubuntu) is perfect on every computer (thus, the clicking). In fact, I'm sure it's not. But it seems to be getting better.

Front mic is the internal mic.
Mic is the external mic.

Yes, your Pangolin from last year has a similar set-up.

---

