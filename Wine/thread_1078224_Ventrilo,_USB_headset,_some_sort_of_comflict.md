---
title: "Ventrilo, USB headset, some sort of comflict?"
date: 2009-02-23
forum: Wine
---

### Post by Zoquara on 2009-02-23
So, I got a USB headset (Logitech Premium USB Headset 350) and am attempting to set it up for use with Ventrilo...

I can hear, but not talk... OR, I can talk, but not hear.. depending on having Direct Sound checked (it has to be checked on output for me to hear)... To be honest, I'm not even sure what all I've tried... In my System>preferences>sound settings, everything is set to USB... I added that one file to the System32 file (part of installing Vent in Wine), and have played with various sound settings for probably 5 or 6 hours... 

Ubuntu 8.04
Not sure what Wine/Vent versions off the top of my head... whatever the newest ones are...
Sorry if this makes no sense.. I'm kinda brain-numb now :(

---

### Post by Bölvaður on 2009-02-23
There are few things to consider.
Firstly trying both Alsa and Pulse for WINE. With Pulse you use "pulse audio device chooser" ( padevchooser ) you can set sound for WINE up with more of a hand on approach.

Then try the headset with other program, preferably a native one, like team speak. If it works then having same settings for WINE should make vent work (with correct redirection in a way windows does sound).

---

### Post by Zoquara on 2009-02-23
I've been using both Pulse and Alsa...
I'll try getting it working in something else in the morning..

For some reason, I also don't have sound from anything playing in Firefox... /sigh

---

### Post by Bölvaður on 2009-02-24
Note that you are unable to use ALSA at same time as OSS audio. So you will have to make sure you got everything set to ALSA or pulse under System &#8594; Preferences &#8594; Sound

There seems to be less problem with sound in 8.10 and probably even better 9.04 when it comes out (you can go alpha test it if you are brave enough.. and there needs to be some more warnings about alpha testing).

Good luck

---

