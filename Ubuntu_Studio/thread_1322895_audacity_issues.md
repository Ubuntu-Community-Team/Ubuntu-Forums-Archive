---
title: "audacity issues"
date: 2009-11-11
forum: Ubuntu Studio
---

### Post by sp00ky_812d on 2009-11-11
hey all

For one reason or another audacity will not record more than a little less than four seconds. It just stops recording and freezes, for want of a better term, until I hit stop and it will only play back around four seconds of audio... any ideas?

---

### Post by sanderella on 2009-11-11
I can't get Audacity to record at all. Playback is fine. I'll be grateful to see any help on this thread. (Worked fine on Ubuntu 09.04)

---

### Post by judge jankum on 2009-11-11
I'm using Ubuntu 9.04 and had the same problems...I removed Audacity 1.3.7 and installed this one and it fixed it..                 audacity_1.3.5-2+lenny1_i386.deb
may not work for everybody but did for me..

---

### Post by sanderella on 2009-11-14
bump

---

### Post by sgx on 2009-11-14
> **sanderella said:**
> I can't get Audacity to record at all. Playback is fine. I'll be grateful to see any help on this thread. (Worked fine on Ubuntu 09.04)
Here are a few ideas
Double check preferences in both your i/o apps, as defaults can change in new releases.

If recording in audacity from a jackd routed source, you must start recording, then press pause, then go to your connections gui, qjackctl, qjackconnect, patchage, whatever you use, and the audacity portaudio icon should now be visible, connect to it, and press pause again to resume recording. 

There should be an alsa setup app, mine is alsaconf. Run it after a reboot, and before you do anything else. Then try a recording.

Blacklist all but the main soundcard. (run the lsmod command, look in the
sound area for module names to put in the textfile 
/etc/modeprobe.d/blacklist. 

Mine has

blacklist snd-usb-audio
blacklist snd_intel8x0
blacklist ath5k
blacklist mac80211

I use an maudio 24/96 pci card, not the others.

Make sure you have the input source you want specifically selected.


Alsa 1.21. may not be your friend. If you have it, and nothing works, you
might roll that back to 1.20 or earlier.

Also, the interactions between web apps using sound, and the various sound systems, are probably alpha-testing level, I would always start a new session, or reboot after going online.

And there are mysteries in the pulseaudio camp. Blanket statements that 'pulse or libpulse can't be the problem', made by people who don't code jackd, alsa, wine, or pulse, are only good for keeping warm and fuzzy feelings alive. It can be part of a seemingly unrelated problem, bottom line, any software that is beta or alpha that you don't -->need, has no business on your hard-disk. My /usr folder is under 600 meg, kde and wine included, and getting smaller as I verify certains things are useless to me.

Try timemachine for a simple recording of some jackd source, if that works, you narrow down the possible list of villains.

Go through synaptic, and delete anything that you don't use, and that you know is not a system file. 

I went through the list of services run on startup, and google has links to verify ones that are just wasting energy for musicians.

Good luck!

---

### Post by sanderella on 2009-11-16
Thank you for this comprehensive list of possible solutions. I'll work through it, and maybe get some help from my local LUG.:)

---

