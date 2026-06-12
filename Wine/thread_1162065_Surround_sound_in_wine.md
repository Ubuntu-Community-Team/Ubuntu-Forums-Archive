---
title: "Surround sound in wine?"
date: 2009-05-17
forum: Wine
---

### Post by LoloftheRings on 2009-05-17
Hi, I just bought a Logitech X-540 5.1 surround speakerset, and I was hoping to get surround sound to work with wine. I generally want this to work for Diablo 2 and Warcraft 3. In the sound configuration of Diablo 2, the '3d sound' option is greyed out. In Warcraft 3, it's no surround sound either. Maybe I need some wine or alsa/pulseaudio configuration or is it not implented yet?

Edit: After changing settings and looking around, I noticed that the center speaker is playing the rear lines.. something isn't going right..

---

### Post by lightstream on 2009-05-17
So does your surround sound work ok outside Wine, eg in music player etc?

---

### Post by LoloftheRings on 2009-05-18
I've been trying around again, following tons of guides. When I run the speakertest tool, I see that the front speakers are working, center not, surround is spread over center and front.
Kinda strange, maybe I connected something wrong..
It doesn't work on windows either, with a soundmax configuration tool. Same effect.

---

### Post by lightstream on 2009-05-18
oh you definitely got that wired up wrong... 

just play some music in music player, right click on the volume control icon to open the mixer controls. Then just mute all channels but one in turn ie first mute Rear and Center, then make sure left and right front sound correct, next unmute Rear and mute Front, etc etc

hope this makes sense, hard to write down what I mean!

---

### Post by LoloftheRings on 2009-05-18
I got it to work on Windows, using a Soundmax tool which was shipped with my motherboard. It works on Windows, but not yet on Linux. I really want it to work, I hate rebooting!

The tool generally asked me every time I plugged in a cable, what exactly I plugged in. After following the prompts, it worked (and I found out my rear speakers were put down reversed xD)

After sliding a lot of sliders in the alsamixer, I got even more confused. The center reacted very strange to line-in, and the left and right speakers reacted to the surround slider..

ARGH!

Edit: maybe this thread should be moved to hardware..

---

### Post by LoloftheRings on 2009-05-18
Got it to work, but after googling around for a long time, I discovered surround is not (yet?) supported in wine. Too bad, reboot will be required for me for surround gaming.. :(

---

