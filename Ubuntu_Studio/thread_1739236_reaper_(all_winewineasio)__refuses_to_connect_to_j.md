---
title: "reaper (all wine/wineasio)  refuses to connect to jack clients"
date: 2011-04-25
forum: Ubuntu Studio
---

### Post by bluesscream on 2011-04-25
Just ran into troubles with natty/jack/wine/wineasio/reaper.
Reaper or other mswindows audio applications open and get wineasio information, show up in jack's connections window too but refuse to be connected to clients.
Here I was testing 11.04 64bit, several kernels, jack 1.9.7, tried wine 1.2, wine1.3, wineasio 0.9.0 and last git w/o success.
It neither works with firewire as you see in the screenshot, nor with alsa onboard hda intel.
ll genuine linux audio works fine. Am I overlooking some configuration stuff?
Any suggestions are wellcome

Best regards 
bluesscream

---

### Post by sgx on 2011-04-25
If you are looking to record music, I would go all 32 bit for now. The fates have managed to corral many of the the biggest audio issues (on any platform) all in one screenshot and post. :) Falks computer is broken, so it may take some time for his repos to take shape as he desires. Tango Studio is getting many good comments, so that may be a good option in the meantime. Also, a barebones linux without any jackd or pulse, is a good way to start from the ground up using jackd 2 without pulse-audio, add the latest alsa and wine, and go from there. There are some Puppy linux distros based on Lucid, that would be good candidates. The Puppy package manager is different from synaptic, but handles .deb files well. Not many dependencies needed to manually set up such a system. Main, Multiverse, and Universe are in their default repos in most cases. A 9 minute video tour of a good one is here:

[http://macpup.org/](http://macpup.org/)

Does the current reaper setup record and play and render its own tracks? If I get inexplicable issues with these, I start jackd with
jackd -d alsa -r 44100, then start qjackctl, then with the reaper
folder in /home/user  run wine reaper/reaper.exe It almost always works. Maybe throw in a killall pulseaudio, some details here:

[http://ptspts.blogspot.com/2009/09/how-to-get-rid-of-pulseaudio-on-debian.html](http://ptspts.blogspot.com/2009/09/how-to-get-rid-of-pulseaudio-on-debian.html)

Cheers

---

### Post by bluesscream on 2011-04-26
Figured it out :D
Malefactor was last wineasio (0.9.0). Today I replaced /usr/lib32/wineasio.dll.so by a copy from a working lucid installation and reaper and other windows programs connect automatically in jack.
For audio with Wine/wineasio Natty seems not to be the first choice - I get poor buffer/xrun ratios.
The same setup is running here smoothly under Lucid.

Tx sgx for your suggestions, my next experimental project will be a rolling release - but not for music production, therefor I'll stay with ubuntustudio lucid and falktx' repos

Best regards
bluesscream

---

