---
title: "Use M-Audio Micro with Ubuntu Studio?"
date: 2009-09-30
forum: Ubuntu Studio
---

### Post by Mike_IronFist on 2009-09-30
I have an M-Audio Micro (It's basically a USB soundcard) that came with my session keystudio keyboard. I was wondering how I could use this in Ubuntu. Plugging it in doesn't mean it "just works" like most stuff does with Ubuntu.

---

### Post by solarbird on 2009-10-01
The docs at M-Audio say it presents as a USB microphone to WInXP and Vista, but also imply that it only does so *after* the Windows drivers are loaded, which further implies that it might not present as such if you *don't* have drivers. (And in that case it would be 1. weird and 2. proprietary.) Have you tried just treating it like a USB microphone?

If you're using JACK, there're instructions here for using USB microphones specifically with Ardour (but really they're the same for using it with anything that uses JACK):

[http://ubuntuforums.org/showthread.php?t=449974](http://ubuntuforums.org/showthread.php?t=449974)

---

### Post by kayosiii on 2009-10-01
Generally speaking almost all usb-1.x based soundcards work out of the box almost all usb-2 soundcards do not. 

Either way details on which usb soundcards are supported, what works and what doesn't can be found at [http://www.alsa-project.org](http://www.alsa-project.org)

[edit] Well that is the usual spot - but I don't see any info there

---

### Post by solarbird on 2009-10-09
[Here's the unofficial list of ALSA-supported hardware]("http://www.alsa-project.org/main/index.php/Matrix:Main"). There's no mention of the M-Audio Micro on the [M-Audio support list]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio") tho'.

---

