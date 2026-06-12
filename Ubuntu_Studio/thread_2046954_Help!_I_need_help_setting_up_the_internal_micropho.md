---
title: "Help! I need help setting up the internal microphone in my Ubuntu Studio install"
date: 2012-08-23
forum: Ubuntu Studio
---

### Post by xaegis on 2012-08-23
Hello, I have a fully functional install of Ubuntu 12.04 and I just installed in a seperate partition Ubuntu Studio. The microphone doesnt seem to work. It seems to move a little when I first open Media Playback/Pulse Audio Volume Control but then the volume indicator for the input/internal microphone just stops after about 3 seconds.

Can anyone please help me set this up properly?

Thanks,


:)

---

### Post by CrocoDuck on 2012-08-24
Hi. I've found volume applets a little buggy on this release. Have a try by setting levels (and/or other things) with alsa mixer. In a terminal:

```
alsamixer
```use F6 to select the device, right/left arrows to navigate and up/down arrows to set levels.

---

### Post by xaegis on 2012-08-24
Ok, so now that my mic is recording apparently, I cant get ANY sound out of speakers or headphones! :(  *sigh*

---

### Post by xaegis on 2012-08-24
Hummmm.. ok I see what they were trying to do by lowering the barrier to entry with the defaults and ALSA/Pulse Audio Just working. But setting up a jack server is still just as necessary, once that was done all I had to do was go open the Totem application and Firefox adn Rhythmbox then go to "Sound Settings" and select "Jack Sinc (pulse Audio jack Sink)"  for all the applications I use as well as the Alsa plug-in. Man all the audio sounds Soooo much better with the Low Latency Kernel but the Menus really need some love for Ubuntu Studio. I sooo prefer the Default Ubuntu UI, xfce runs GREAT! but as a UI there is sooo much repetition and wasted space and dead ends. I really wish Ubuntu Studio had gone with Unity as a UI. Although I am really loving the resource use of the system now. it doesnt overheat as quickly, but it still feels almost as snappy as Unity.

SOLVED!

:D

---

