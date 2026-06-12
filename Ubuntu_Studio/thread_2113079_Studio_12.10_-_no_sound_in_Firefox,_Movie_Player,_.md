---
title: "Studio 12.10 - no sound in Firefox, Movie Player, Rosegarden - sound ok in other apps"
date: 2013-02-06
forum: Ubuntu Studio
---

### Post by callmebruce on 2013-02-06
I recently installed Ubuntu Studio 12.10 64 bit, doing a clean install. I have an ancient Lenovo ThinkCenter M55 with just an onboard Intell sound card.

It seems that applications using JACK have good sound. I configured Audacity to use JACK, and can import tracks and hear sound. Audacious works. Ardour works. I was able to use an adapter and plug an electric guitar into the mic port and rakarrak worked (or guitarx? I need to try again). Virtual synthesizer gives sound, as does hydrogen.

However - I can't figure out how to get sound working in Movie Player, Firefox and Rosegarden. It seems applications that I can configure to use JACK just seem to work, but applications I can't figure out how to set up just do not give sound. Don't think it's a hardware thing as sound works in several applications (and I used Mixer to make sure nothing was muted).

I tried to follow the Introduction to Audio on the Ubuntu Studio documentation page [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204]("https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204") - but get stuck at the Pulse Audio to JACK Bridge section (and am not sure if it applies in 12.10

Any help in getting one or two applications to give sound?

---

### Post by callmebruce on 2013-02-06
Well, VirtualSynth no longer produces sound. Rakarrak works when I plug my guitar into the sound card port in the back of the desktop, but no longr works when I use the front mic. port.

---

### Post by callmebruce on 2013-02-06
Sorry to reply to my own post. I rebooted off my flash drive with Ubuntu Studio 12.10. Sounds worked fine in my web browser and music player app. I rebooted and have sound. Think I need to read some manuals and tutorials. I must have messed up some sound settings or had conflicting applications open.

---

### Post by ttoine on 2013-02-07
[https://help.ubuntu.com/community/UbuntuStudioPreparation#Pulse_Audio](https://help.ubuntu.com/community/UbuntuStudioPreparation#Pulse_Audio)
Have a look at that. The problem is that on the flashdrive, jackd may not be running, while it run once installed.

Installing "pulseaudio-module-jack" may just work fine.

---

