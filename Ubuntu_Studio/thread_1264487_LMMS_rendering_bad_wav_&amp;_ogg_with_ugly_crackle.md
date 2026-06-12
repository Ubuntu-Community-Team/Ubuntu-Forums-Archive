---
title: "LMMS rendering bad wav &amp; ogg with ugly crackle"
date: 2009-09-12
forum: Ubuntu Studio
---

### Post by yours-truly on 2009-09-12
Hi,

I have got some trouble with LMMS.
It runs all fine in live mode, even in high quality mode with nice clean filter sweeps.
But the rendering has ugly crackles an something like a digital noise in it.
I've tried all different render settings without any luck.
Disabling voices one after an other doesn't help me either.
Sometimes the rendered wav or ogg file is just half rendered an the rest is empty with full file length.

I would be glad to read any suggestions, 
the ubuntu forums in my native language (german) didn't brought up any help.

With best regards,
yours-truly.de

---

### Post by BCtom on 2009-10-12
> **yours-truly said:**
> Hi,
 But the rendering has ugly crackles an something like a digital noise in it.
I've tried all different render settings without any luck.
Disabling voices one after an other doesn't help me either.
Sometimes the rendered wav or ogg file is just half rendered an the rest is empty with full file length.
 

This could be one of  hundreds of problems with your system. Sound and Linux/Ubuntu can be a tricky thing.

When I first upgraded to Jaunty, and had to learn PulseAudio and all of its little issues, and I was getting something similar to your issues. I found that just going through the settings, trying different patterns of sound fader positions and switches, eventually got it to more or less  studio quality sound. For me it was my settings, and it didn't seem to have anything to do with any of the audio codecs I was using. But I was getting a lot of clipping when rendering my songs down into mp3.  I just increased my sample and bit rate to keep the quality better.

Trial and error. 

I hope you get it figured out. I think LMMS is a very cool program, and a boon for the open source community.

---

### Post by yours-truly on 2009-10-20
Hi,

thank you for your Tips. I doublechecked all configurations from the very beginning and found some missconfiguration. 

If someone has the same or equal problems check this:

Export your file and try playing it on your external mp3 player or another computer. If it sounds clean on another computer you have to check your soundsetup on ubuntu.

Check that you have always the right output settings.
In Audacity:
Preferences E/A Audio might be "Alsa Pulse"
Preferences Quality 44.100khz and 32 Floating

Problem solved, thank you very much
btw: Yes, LMMS is tricky, but a realy good tool.


Best Regards,
yours truly

---

