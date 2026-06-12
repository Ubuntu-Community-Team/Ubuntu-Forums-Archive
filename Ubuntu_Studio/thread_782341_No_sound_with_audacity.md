---
title: "No sound with audacity"
date: 2008-05-04
forum: Ubuntu Studio
---

### Post by philidox on 2008-05-04
I am having a no sound issue with audacity.  I have been thru the preferences and select all the different types of audio port no luck.  However there is one thing worth noting is that some of the port audacity will visually play the sound while most of the audio port it will just give me an error message.  Please help!

---

### Post by Stochastic on 2008-05-05
okay, which options visually play the file?  also, run alsamixer and double check all the levels (and that they're not muted).  lastly, make sure firefox and all other audio apps are closed while troubleshooting any audio.

---

### Post by philidox on 2008-05-05
> **Stochastic said:**
> okay, which options visually play the file?  also, run alsamixer and double check all the levels (and that they're not muted).  lastly, make sure firefox and all other audio apps are closed while troubleshooting any audio.

O my goodness never mind it is fixed!.  I just did an update to the latest ubuntu distro 8.04 and switch the playback device to ALSA: default.  I can even run audacity with other sound programs and they will run all at once!  Which is something I could never do before in the past it would just lock up the port.  Go figure.  Here is a screenshot of my settings

---

### Post by Azraelthe7th on 2008-05-11
What's your system's sound configuration?

---

