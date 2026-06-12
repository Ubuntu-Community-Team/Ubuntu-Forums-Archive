---
title: "Screencasting on 8.10"
date: 2009-01-09
forum: Ubuntu Studio
---

### Post by Bios Element on 2009-01-09
Now I know this topic has been done to death but I cannot seem to figure out how to get this to work.

What I need is a way to screencast video's with pulseaudio sound (Or some workaround that doesn't involve breaking pulseaudio). I know recordmydesktop doesn't like pulseaudio and I have no idea how to get around that. Also it'd be nice to have a way to record video from a webcam as well if that's at all possible.

Thanks in advance!

---

### Post by andr3w on 2009-01-27
> **Bios Element said:**
> Now I know this topic has been done to death but I cannot seem to figure out how to get this to work.

What I need is a way to screencast video's with pulseaudio sound (Or some workaround that doesn't involve breaking pulseaudio). I know recordmydesktop doesn't like pulseaudio and I have no idea how to get around that. Also it'd be nice to have a way to record video from a webcam as well if that's at all possible.

Thanks in advance!

Yeah, I'd like people to start actually answering this question too! :D

---

### Post by neu2buntu on 2009-01-27
you will need to use jack the frontend being qjackctl. and any jack related dependencies too. it takes a bit of setting up tho,but worth it.  it wont break puleaudio as far as i know just temp disable it until you stop and quit qjackctl. i use it to make screencasts of demos i make in lmms,ardour.nearly all the mucic creation apps in ubuntu and some windows ones also.

---

### Post by MaindotC on 2009-03-31
I just use ustream.tv to record from my webcam.  I know that doesn't really solve the problem but it's a decent workaround.  I have the skype-approved webcam so it works perfectly w/ 8.04.

---

### Post by Amazona aestiva on 2009-05-16
Hi!

I still use Intrepid and I could get recordmydesktop to record sound too.

Make sure Sound Device is set to "DEFAULT" in recordmydesktop advanced options(without quotes)

Then open up your volume control panel and add the switch called "Mix" and make sure it is enabled.

Select the capture device of ALSA. It's "Capture: ALSA PCM on front:0 (ES1371 DAC2/ADC) via DMA (PulseAudio Mixer)" for me, There set volume of Master nearly on top but a bit lower... about 4/5

That should do the trick;)

Regards,

---

### Post by neu2buntu on 2009-05-16
> **Amazona aestiva said:**
> Hi!
..
I still use Intrepid and I could get recordmydesktop to record sound too.

Make sure Sound Device is set to "DEFAULT" in recordmydesktop advanced options(without quotes)

Then open up your volume control panel and add the switch called "Mix" and make sure it is enabled.

Select the capture device of ALSA. It's "Capture: ALSA PCM on front:0 (ES1371 DAC2/ADC) via DMA (PulseAudio Mixer)" for me, There set volume of Master nearly on top but a bit lower... about 4/5

That should do the trick;)

so it is actually possible to record the desktop audio without the need for "jack"......good to know as i spent ages trying to resolve this problem,and ended up using "qjackctl" for my audio.       well anyway glad you posted as this will help others!!!....

Regards,
.....

---

