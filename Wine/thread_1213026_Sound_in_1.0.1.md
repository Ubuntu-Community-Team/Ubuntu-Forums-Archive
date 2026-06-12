---
title: "Sound in 1.0.1"
date: 2009-07-14
forum: Wine
---

### Post by rusty377 on 2009-07-14
Hello,

I have installed Wine and am having issues with Nvidia (motherboard mounted) Soundcard with ALC883 chip. I have removed the PulseAudio drivers and am now only using ALSA system drivers. When in winecfg in Audio section - no matter which driver or combination I select when I press the Audio Test button it replies "Audio test failed", of course there has never been any sound in Wine on my system. I do have intermittent sound failure outside of wine.  Any help appreciated.

Trying to get Reaper recording software to work via wine.

Cheers,
Rusty

---

### Post by akudewan on 2009-07-14
I have the same sound card. I've noticed that usually the npviewer.bin process (used to play flash in firefox) blocks the soundcard. Killing it enables sound in Wine for me.

---

### Post by rusty377 on 2009-07-14
akudewan,

I cannot find the npviewer.bin process at all. Are you using the system monitor to view processes? Any other ideas? This sound system is builtin to an HP a1410n system a few years old- is yours built-in and did you modify around the Pulseaudio in JJ?

Thanks again,
Rusty

P.S.

All of a sudden the wine audio config is working and I can get the bloop bloop sound on the test button. Hmmm..must be a problem with Reaper now?

Thanks

---

### Post by akudewan on 2009-07-14
npviewer.bin will show up in the process list of if there's Flash content running in the browser. I just use the command *killall npviewer.bin* from the command line.

I use pulseaudio, and my soundcard is an on-board ALC662, not ALC883 (I forgot!)

The fact that sound started working with Wine may mean that there was some process blocking the sound device after all.

If the program is still not functioning properly, it may be due to some other problem. Wine isn't perfect...

---

