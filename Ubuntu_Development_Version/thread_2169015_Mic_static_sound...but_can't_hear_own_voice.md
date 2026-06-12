---
title: "Mic static sound...but can't hear own voice"
date: 2013-08-20
forum: Ubuntu Development Version
---

### Post by Moony22 on 2013-08-20
Hello,

I am running 64 bit Saucy Salamander, with PulseAudio, AlsaMixer, and also pavucontrol. 

My microphone worked fine in Linux Mint 15. But now, all I hear (On skype OR recording) is a static noise, which increases slightly if I breath into the microphone.

I have looked into this a lot, and tried many things. Some of these include:

[B]Increasing the volume in "paman" of my source.

Increasing everything for every sound card in alsa mixer.

[This post. ]("http://ubuntuforums.org/showthread.php?t=1860715&page=2&#15")(Did not work because the pulseaudio daemon wouldn't start, so I had to delete the .pulse directory).

[/B]I would really appreciate some help with this, as I do use my microphone a LOT. I really don't want to have to switch distro's for every task I want to do. If you need any more info just tell me and I can supply that. 

Thanks,
Moony22

---

### Post by jfernyhough on 2013-08-20
Within pavucontrol, check under Configuration that your audio is set to Duplex. Under recording, make sure that the input device is not Monitor (if it is, set it to your sound device).

---

### Post by Moony22 on 2013-08-20
My microphone is set to "Analogue Stereo Duplex", and I have definitely chosen the correct device.

---

### Post by xc3RnbFO8P on 2013-08-20
What option do you get in Skype> Option> Sound Devices, just pulseaudio server ?

---

### Post by Moony22 on 2013-08-20
Yes, just pulseaudio (local).

---

### Post by xc3RnbFO8P on 2013-08-20
Did you install Skype from Ubuntu Software Center?

---

### Post by Moony22 on 2013-08-20
Yes.

---

### Post by xc3RnbFO8P on 2013-08-20
try:
> sudo dpkg --configure -a
> sudo apt-get update && sudo apt-get upgrade
and restart

---

### Post by Moony22 on 2013-08-20
Well, at least my voice is heard now. Thank you for that answer. However, I can only hear my voice if I turn the recording volume up to 153% in pavucontrol, and when I do so, I can hear a static noise quite loud, which is very annoying. This did not happen with mint, and I tested with another microphone which works fine. 

By the way, this is not just with skype, it happens with the audio recorder, and with:
```
gst-launch pulsesrc ! pulsesink
```
Perhaps I'm asking too much, but I would very much appreciate help with this further static issue.

---

### Post by Moony22 on 2013-08-22
Bump.

---

### Post by Sworddragon on 2013-08-23
I'm wondering if this is related to this problem: [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1214633](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1214633)

---

