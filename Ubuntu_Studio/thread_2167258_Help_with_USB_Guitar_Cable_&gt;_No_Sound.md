---
title: "Help with USB Guitar Cable &gt; No Sound"
date: 2013-08-13
forum: Ubuntu Studio
---

### Post by td-potter505 on 2013-08-13
I have read through several threads and have tried making the setting changes, but I still can't get any sound to come through my laptop running 64 bit Ubuntu 12.04. I found a couple of terminal commands in another thread and have posted the results below. Not sure why this one is so confusing to me. Here are the results. Please let me know what you suggest. Thanks.
tom@tom-N53Jq:~$ arecord -l|grep -v "Subd" && aplay -l|grep -v "Subd"
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
card 2: Adapter [Rocksmith USB Guitar Adapter], device 0: USB Audio [USB Audio]
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
card 0: Intel [HDA Intel], device 1: ALC269VB Digital [ALC269VB Digital]
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
tom@tom-N53Jq:~$ cat .jackdrc
/usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Chw:2 -Phw:1

---

### Post by jejeman on 2013-08-13
Try to see if it works without JACK. Use Audacity or similar, set input to be the USB card.
Check in Alsamixer if capture fader is not muted and turned up. Also if there is a switch to select correct input.

---

### Post by td-potter505 on 2013-08-13
I installed Audacity (and all of the plug ins listed in the software center), I can select the USB cable as an input and it looks like something is recorded - blue lines get wider when I play. However, I have selected every output option and I cannot hear anything. I also tried to export the track and I couldn't hear anything from the recorded track. I am not having any other issues with the sound.

---

