---
title: "Removing PulseAudio"
date: 2014-02-11
forum: Ubuntu Studio
---

### Post by justbinfishin on 2014-02-11
Short intro: I installed ubuntu 12.04 yesterday. After demo-ing Windows 8.1 (I need a Microsoft live account just to log into my own computer?!?) on my desktop & hearing plans for Windows 10 to be cloud-based, I decided that Microsoft will never get another dime of my money.

Anways, I installed PulseAudio Equalizer, and it caused immediate problems in my music  playback exerience (lags and scratchiness every time I change the volume of a playing song). I ran sudo apt-get autoremove pulseaudio, and then sudo apt-get purge pulseadio.  That didn't work, pulseaudio is still installed and still works. So I looked it up on this forum and followed the directions on [http://ubuntuforums.org/showthread.php?t=841911](http://ubuntuforums.org/showthread.php?t=841911) .  I ran sudo apt-get install esound, followed by sudo apt-get remove pulseaudio, and purged it again.  The app is still installed... sudo apt-get purge returns "pulseaudio is not installed, so not removed". 

What gives?

Thank you

Justin B

---

### Post by jejeman on 2014-02-12
Installing esound to remove pulseaudio is nonsense.
You don't need to uninstall pulseaudio, just turn it off.
Give
```
dpkg -l | grep -i pulse
```

---

### Post by Bucky Ball on 2014-02-12
Yep, that link you provided is from 2008 and well obsolete, as is esound. Now you'll need to get rid of that. 

Suggest you remove esound, reinstall Pulseaudio and post a thread on the problem with the equaliser. Or remove Pulse and esound and use ALSA (which is what you do if you remove Pulse).

What release are you using and please confirm you are using Ubuntu Studio. If you are you could always use jack for everything. ;)

---

