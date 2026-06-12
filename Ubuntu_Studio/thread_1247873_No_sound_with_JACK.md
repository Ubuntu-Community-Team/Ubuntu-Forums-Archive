---
title: "No sound with JACK"
date: 2009-08-23
forum: Ubuntu Studio
---

### Post by graphicsxp on 2009-08-23
Hi,
I've spent hours trying to get my Studio applications working with JACK but I still don't have any sound from any of them (I've tried Ardour, Hydrogen and SooperLooper).

Here's a [screenshot]("http://graphicsxp.s3.amazonaws.com/Screenshot.png") of Hydrogen running and playing a song. You can also see JACK settings. Note that hw:0 is my SoundBlaster Live 5.1.  

So since I'm new to recording on Linux maybe I'm missing something. Can someone help me ?

It's important to note that I have sound with ALSA in these applications mentioned above and that there is no sound issues with my computer for playing audio or movies. The issue is only with JACK.

Thank you
Sam

---

### Post by graphicsxp on 2009-08-23
Posting here must have had some kind of mystical effects... I've found the solution 2 minutes later !!! :)

I clicked on the volume control in my taskbar. Then in the list of devices I have :

SBLive 5.1 (Alsa mixer)
SigmaTel STAC9708,11 (OSS Mixer)

All volumes were at max under SBLive so I had not thought the problem could come from here. But then I looked under SigmaTel and PCM-2 was mute. I've turned it to max, and now the sound works in every applications with JACK.

If someone could explain what this PCM-2 thing is, feel free ! Otherwise, I'll live with that anyway.

---

