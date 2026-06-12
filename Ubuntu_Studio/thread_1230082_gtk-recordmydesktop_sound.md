---
title: "gtk-recordmydesktop sound"
date: 2009-08-03
forum: Ubuntu Studio
---

### Post by sdlynx on 2009-08-03
I am not getting sound with gtk-recordmydesktop.  I have tried numerous things.  Also, my mic isn't working anymore (only on linux).  I have tried numerous different things, even jackd (which refused to make any noise at all).  The sound used to work great (pcm + capture[mic]) and I didn't change any settings for gtk-recordmydesktop.  Ideas?

---

### Post by igorzwx on 2009-08-03
It was kernel update (security problems, pulseaudio vulnerability, etc.)

commands (on Terminal)

aplay -l

lspci -v

lspci > hardwareinfo.txt


The last command will produce a text file " hardwareinfo.txt"


Install several Ubuntu 9.04 on the same box

try:

1. ALSA + esound (without pulseaudio)

2. OSS4 (without alsa and pulse)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

one of these solutions may work


**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

### Post by sdlynx on 2009-08-04
Is there an easier way than changing from ALSA to OSS/ESD....?

P.S. I tried to switch but it got too complicated for me.

---

### Post by mocha on 2009-08-07
> **sdlynx said:**
> Is there an easier way than changing from ALSA to OSS/ESD....?

P.S. I tried to switch but it got too complicated for me.

Yeah, use my guide, [http://ubuntuforums.org/showthread.php?t=986966]("http://ubuntuforums.org/showthread.php?t=986966")

---

### Post by sdlynx on 2009-08-07
I tried jackd, and have already tried it.  Unfortunately, I get no sound whatsoever when using it.

---

