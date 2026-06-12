---
title: "Darter system sound replaced by Front?"
date: 2007-09-15
forum: System76 Support
---

### Post by balshan on 2007-09-15
I'm not sure exactly how sound output works on the Darter, but I'm having a little bit of an issue here, which is probably related to the following thread, but I can't find any solution to my problem there:
[http://ubuntuforums.org/showthread.php?t=489125](http://ubuntuforums.org/showthread.php?t=489125)

For the longest time, I've "suffered" the common problem of the sound hotkeys not working, and the speaker volume control having no effect. If I want to adjust the system volume, I have to open KMix (I'm on Kubuntu Feisty) and adjust the Front channel volume. When I first used the Darter, the system volume (listed in KMix as "PC speaker") worked fine, along with all the hotkeys, but that hasn't been the case for a while.

I've read that this is a software issue, and that you can adjust some setting in Gnome to fix it, but I can't find any such setting to adjust in the K sound controls, and I have no idea which config file to edit or where it is stored.

The reason all this is an issue is that I got a cheap little USB sound card that outputs 5.1-channel audio for my surround sound speakers. It has its own volume control, and when I use that volume control, the response is that the "PC speaker" channel changes. Unsurprisingly, therefore, I get no sound output to this sound card, because the sound isn't being output on the "PC speaker" channel anyway, but rather on the Front channel. How do I fix this so the sound is going to the right place, so I can stop feeding stereo sound through my center and woofer channels?

---

### Post by thomasaaron on 2007-09-17
Are you using a System 76 computer, and if so, which one?
Also, we've had other key-mapping problems with KDE. That is one of the reasons we do not support it. It could be that an update that came down for KDE hosed your key-mapping.

That said, if you were using GNOME, I'd have you go to System>Preferences>Sound. There you can set the Default Mixer Device (all the way at the bottom) to the device you want to control with your sound keys. I don't know if KDE has that or not.

---

