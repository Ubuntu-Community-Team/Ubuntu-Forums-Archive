---
title: "Zoom H4N with Audacity + Ubuntu 10.04?"
date: 2010-05-03
forum: Ubuntu Studio
---

### Post by JitsuDan on 2010-05-03
Hi,
I'm trying to use my Zoom H4N to record via the USB interface in Audacity on 10.04.
However, when I press record, the timer just flickers over zero seconds and does not record anything.

Has anyone managed to get this working?  If so, please share what you did.

Any advice appreciated.

Thanks.

---

### Post by ajgreeny on 2010-05-03
What exactly are you trying to do?  It sounds as if you are trying to use the Zoom as a microphone, but I may be wrong about that.

If you are using the Zoom to record and then trying to get the sound into audacity using "line in" it is probably just the settings in **pulseaudio-volume-control** or **sound-preferences** that need sorting out a bit, not easy now, I admit, but it can be done.

Apologies if I have got the wrong problem, but tell me more, if so.  I use audacity a lot with a mic, and also to record sound card output in general, so might have some clues to give you.

---

### Post by LuridCinema on 2010-05-03
I have the Zoom myself. I love it. Why not record onto the SD card then import ? Ubuntu will "see" the H4n as a drive OR just plug the SD card into a reader and copy onto your hard drive.

---

### Post by JitsuDan on 2010-05-03
Hi,
I will be using it as a standalone device as soon as I get hold of a larger memory card.  I only have 1GB at the moment.

Just to clarify, I'm using the H4N as a mic to record acoustic guitar directly into Audacity.

I've attached an image to show what's going on.  The second part just shows where it's getting 'stuck'.
The error message at the bottom comes up if I stop the recording and try to start it again.

Many thanks for your advice.

---

### Post by ajgreeny on 2010-05-03
Try changing the recording device to pulse.  That's what seems to work for all my uses of audacity now

---

### Post by azurplex on 2010-06-30
> **JitsuDan said:**
> Hi,
I will be using it as a standalone device as soon as I get hold of a larger memory card.  I only have 1GB at the moment.

Just to clarify, I'm using the H4N as a mic to record acoustic guitar directly into Audacity.

I've attached an image to show what's going on.  The second part just shows where it's getting 'stuck'.
The error message at the bottom comes up if I stop the recording and try to start it again.

Many thanks for your advice.

The error you are getting says you should check your sample/bit rate settings.
Make sure your project's sample rate and the sample rate mode of the h4n match. Is h4n sending mp3 when audacity is expecting 24/96 or 16/44.1 wav?
Also, When I use the h4n standalone I need to press record once to get monitor mode (record ready) then again to start the recording.
Hope this helps.
I just noticed your project's sample rate is "32 bit float". H4n doesn't do that bitrate.

---

