---
title: "Delta 44 (ice1712) works but very low quiet output"
date: 2008-11-03
forum: Ubuntu Studio
---

### Post by JohnnyNoBueno on 2008-11-03
I have searched everywhere about this problem.  I'm running Ubuntu Studio 8.04 on an AMD 64 3200+, 1G ram, nForce 410, GeForece 6100, and a Delta 44 (ice1712/envy24) sound card.  Everything seems to be functioning correctly but the output levels are way low.  With the DAC's cranked, I have to max out my monitors to hear anything, resulting in a lot of unwanted noise and basically a crap setup.  

Interestingly, I have the same problem with the on board sound.

I have tried various other distros with the same results.  I have tried disabling and enabling the on board sound.  The card works perfectly in other machines with the same OS's.  I don't quite know where to go from here.

Any help would be greatly appreciated.

---

### Post by JohnnyNoBueno on 2008-11-03
bump? :)

---

### Post by surfed on 2008-11-03
> **JohnnyNoBueno said:**
> I have searched everywhere about this problem.  I'm running Ubuntu Studio 8.04 on an AMD 64 3200+, 1G ram, nForce 410, GeForece 6100, and a Delta 44 (ice1712/envy24) sound card.  Everything seems to be functioning correctly but the output levels are way low.  With the DAC's cranked, I have to max out my monitors to hear anything, resulting in a lot of unwanted noise and basically a crap setup.  

Interestingly, I have the same problem with the on board sound.

I have tried various other distros with the same results.  I have tried disabling and enabling the on board sound.  The card works perfectly in other machines with the same OS's.  I don't quite know where to go from here.

Any help would be greatly appreciated.


Have you tried playing with envy24control ? What sound system? alsa jack pulse?

---

### Post by JohnnyNoBueno on 2008-11-04
Thanks for your reply.

I'm using ALSA right now.  Envy24 is my first choice, but after maxing every fader out, I still have a very weak signal.  I've used alsamixer, like the sound troubleshooting post suggests, but no results there either.

The curious thing is that this problem affects any soundcard I put in.  I've tried the on-board audio, a SoundBlaster Live! and the Delta 44, and they all exhibit the same issue.  All the cards I have tested work in my other PC's under Linux.  The other interesting thing is that this problem persists in every distro I've tried it on:  Ubuntu Studio, Musix, 64 Studio, XuBuntu, even W2K.

The original problem was very quiet distorted audio, but I fixed the distortion by using the restricted nvidia drivers for the chipset & video.  Is it possible that something about the 64-bit architecture is making the 24-bit ADC/DAC's interpret the data incorrectly?

---

### Post by thorgal on 2008-11-04
what about your speakers ? have you tested them with another machine ? you said the onboard audio chip is also weak through them. That would be my 1st suspicion. Either the speakers or whatever is in between your card and the speakers (cables, connectors).

---

### Post by JohnnyNoBueno on 2008-11-04
Thanks for the suggestion.

I wish it was that simple.  A couple weeks ago I had to get some tracks mastered, so I threw together an old PIII motherboard (painful) and used it with the same mixer and monitors that I have hooked up right now.  Using the same connections from the Delta 44 to the mixer as right now, I had normal levels going on.  I have swapped cables, used different mixer inputs, used headphones, etc.

---

