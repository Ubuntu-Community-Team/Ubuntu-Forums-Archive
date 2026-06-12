---
title: "Can't get JACK server to run for Rosegarden"
date: 2009-03-22
forum: Ubuntu Studio
---

### Post by syntheticromania on 2009-03-22
I've been trying to get my JACK server running for a couple of days now. Every time I try to run it through Applications -> Sound & Video -> JACK Control it freezes and I have to force quit. Running it from the terminal, I get a warning saying, "Warning: no locale found: /usr/share/locale/qjackctl_en_US.qm" and then I have to force quit the JACK control because it freezes. 
I really have no idea what I'm doing at this point. I tried jackd -d alsa and oss in the terminal and all I get back is that something is already using my playback device, even though nothing but the terminal is running, at least to my knowledge. 
Any help would be greatly appreciated!
Thanks!

---

### Post by af20001 on 2009-03-27
I'm not sure about the locale problem, but for the jackd -d thing in the terminal, make sure in your sound settings that you have selected ALSA as the playback device for everything. You might find that something is set to PulseAudio.

---

### Post by Monona on 2009-03-28
I don't think the error message your getting is the problem.  I get that when I run qjackctl from the terminal, but it runs just fine.  

You installed jackd and qjackctl from the repositories?  What version?  (you can find that out by running "qjackctl -v" or "jackd -V".

To see what's using the soundcard, run:

sudo fuser -v /dev/dsp*
sudo fuser -v /dev/snd/*

Post the output.  Sometimes I have unnecessary programs using my soundcard.  I'm not sure how they get there, but things work once I kill them.

---

