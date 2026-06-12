---
title: "Audacity will not record sound playing through speakers"
date: 2009-08-22
forum: Ubuntu Studio
---

### Post by teamsj on 2009-08-22
I'm running Jaunty and I have Audacity 1.3.7 installed.  I can't get audacity to record what is being played on my speakers.  In preferences I have ALSA default set for recording and channel 2 stereo.  I'm pretty sure I have been through every option for recording, but still can't capture the audio.  ls pci shows my audio as:
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller

Any ideas on how I can record?

---

### Post by trulan on 2009-08-23
It can be done using the JACK audio server - sgx just posted a quick how-to here:
[http://ubuntuforums.org/showthread.php?t=936487](http://ubuntuforums.org/showthread.php?t=936487)

---

