---
title: "Activate HDMI Bitstream Audio passthrough to reciever"
date: 2015-08-25
forum: Ubuntu/Debian BASED
---

### Post by mahesh10 on 2015-08-25
Hi , I'm also facing similar issue in DTS/Dolby output to A/V receiver. I'm a new convert to elementary OS (ahem.. noob) from windows 8 . 
In Windows I use Mediaplayer classic (VLC didn't help me in windows also) to play movie and output it to my receiver through HDMI. In Receiver I get DTS/Dolby based on the media I'm playing.
Whereas inn Elementary OS I'm getting only PCM no matter which channel I play. I've tried using VLC and GNOME M Player. In VLC if I select audio device as HDMI also the output is detected as PCM . In Gnome M player I  tried selecting various audio configuration nothing helped so far. Is there any player which gives bitstream audio out without converting?

Laptop config
 Intel i5 , DELL 

Any help will be great. Thanks in Advance

---

### Post by howefield on 2015-08-25
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by mahesh10 on 2015-08-26
It worked for me. In VLC and SMPlayer I kept the audio out as Alsa and selected various option in the HDMI output device(that had 'without any software process' since I wanted the AV receiver to take care of the processing) one of the option worked in both the players. Thanks all..

---

