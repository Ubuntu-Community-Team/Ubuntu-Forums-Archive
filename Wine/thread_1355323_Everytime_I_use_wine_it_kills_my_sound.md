---
title: "Everytime I use wine it kills my sound"
date: 2009-12-14
forum: Wine
---

### Post by Jguy on 2009-12-14
Hi,

I am using Ubuntu 9.04 64-bit. wine reports: 

> 
jguy@jguy-desktop:~$ wine --version
wine-1.1.34


Everytime I start a wine application, notepad, configuration, doesn't matter, my sound dies computer wide. Whatever was continuously playing sound has to be restarted to gain sound functionality (Banshee, for example)

EDIt: Even restarting it doesn't help. With wine running, all sound is dead. The only sound that works is the system speaker.

right now, the ALSA driver is enabled in winecfg with Emulation Accelaration, and I've tried it with 'Full' with the same results. Is there maybe a driver or package I'm missing? 

Thanks for any light you can shed on the situation.

---

### Post by beastrace91 on 2009-12-15
Are you using pulse-audio or alas in your sound configuration settings in Ubuntu itself?

~Jeff

---

### Post by Jguy on 2009-12-15
I'm not at home currently, but I do believe the Sound Preferences show ALSA.

---

### Post by Bwathke on 2009-12-15
Ive only heard of WINE making it so the application its running it the ONLY sound you hear and when you close it you lose all sound. Never heard it where it goes all together. Have you tried new speakers?

---

### Post by Jguy on 2009-12-15
I don't quite know why it would be the speakers, as the speakers remain untouched throught this....I enter a WINE application, sound died, I close said WINE application, restart the application that was making the sound (Banshee, for instance) and sound returns...

Sound playback in Sound Preferences is set to 'HDA Nvidia VT1708S Analong (ALSA)' and Default Mixer Tracks - Device is set to The same except for '(PulseAudio)' in place of '(ALSA)'. All the rest are set to ALSA. I am using the onboard sound on my motherboard, an ASUS. I am unsure of the specific model, as on this one it is not written on the board.

---

### Post by Exüberance on 2009-12-18
Try setting Wine to mimic XP instead of Vista, then set all your sound options back to normal (use ALSA, you don't need OSS and you don't need padsp or anything).

I was having a problem with WoW where I couldn't get sound no matter what I tried (though I still had sound in other apps, so this might not work), then I tried emulating XP instead of Vista and, that's it, I had sound :)

---

