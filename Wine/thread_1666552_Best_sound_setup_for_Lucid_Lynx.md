---
title: "Best sound setup for Lucid Lynx"
date: 2011-01-13
forum: Wine
---

### Post by Cadeyrn on 2011-01-13
Running wine 1.3(.11 currently) on Linux Mint 9 (AKA Ubuntu 10.04), what is the best sound setup for no glitches (sound delay, sound disappearing, or no sound in one wine app because another wine app is hogging sound, or no sound in one Linux app because wine is hogging sound)?

I've tried winepulse, wine-ALSA (normal wine with ALSA checked in winecfg), and padsp wine-ALSA. I haven't tested padsp wine-ALSA that much, but winepulse doesn't change anything, and wine-ALSA only works properly if I kill pulseaudio, which is a pain and makes me have to restart any sound-needing programs running.

Ones I've heard of that could work are padsp wine-ALSA, padsp wine-OSS, and wineasio (the best version of wine with JACK). Which one would give me the best performance? I'd prefer not to run wineasio if I don't have to, as having a separate repo for wine that's maintained by somebody else can be annoying, especially because that causes APT/Synaptic to block me out of wine-doors and PlayOnLinux.

So far, which sound glitches I get seems to be inconsistent and based on which programs I'm running, for instance, most wine apps have many problems with wine-ALSA running without any help*, but STALKER SHoC's sound runs flawlessly--no delay or losing sound or anything. I would test these setups myself, but the only programs I've confirmed to have these glitches are 3D games, and the only 3D game that hasn't stopped working for me on wine for literally no reason (check it out--no reason at all: [http://bugs.winehq.org/show_bug.cgi?id=25595](http://bugs.winehq.org/show_bug.cgi?id=25595)) is STALKER. So I'm in no real position to extensively test these three solutions.

*"help" being either running "padsp wine" or killing the pulseaudio process.

---

### Post by Cadeyrn on 2011-01-13
Oh, wow. The ONE time I didn't search a forum for duplicates of my topic before posting is the ONE time there are duplicates.

EDIT: Well, actually, of the three topics, one has been resolved by winepulse, which didn't fix it for me, and the other two are not exactly my problem. So I guess this thread is legal.

---

### Post by cogadh on 2011-01-14
There is no single "best" sound setup, especially if you are trying to run games in Wine. Every game is going to be different, as it seems you are discovering. The easiest to deal with it for me has been the regular Wine (unstable from the Wine PPA) combined with Wine's built-in profile functions to create application profiles for each app that needs a different sound driver, leaving ALSA as the default.

---

### Post by Cadeyrn on 2011-01-14
So, I suppose I should have different games be ALSA or OSS depending on which one works better for that game and run it all with padsp because some games won't work properly with ALSA or OSS alone.

---

### Post by cogadh on 2011-01-14
Not necessarily, you don't always need to run it with padsp. Additionally you should try other sound options in Wine beyond ALSA and OSS. A lot of people have reported good results with EsounD (considering PulseAudio is a replacement for EsounD, not really surprising). This is the nature of Wine; often there is no single right answer, you need to try everything to find the best answer for each application.

---

