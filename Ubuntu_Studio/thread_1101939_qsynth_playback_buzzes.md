---
title: "qsynth playback buzzes"
date: 2009-03-20
forum: Ubuntu Studio
---

### Post by le_vainqueur on 2009-03-20
I have Qsynth up an running on my system, but there is buzzing when I play my MIDI keyboard through it.  I have not been able to find a setting to solve this.  I have several soundfonts that I tried, but all of them have the same problem


Any tips?

---

### Post by thorgal on 2009-03-21
increase the buffer size in qsynth.

---

### Post by Stochastic on 2009-03-21
It may also stem from some poor hardware grounding between your midi soundcard, audio soundcard, computer, and midi keyboard.  Though, if it only happens in qsynth this is probably not the case.

---

### Post by le_vainqueur on 2009-03-21
> **thorgal said:**
> increase the buffer size in qsynth.

I increased the buffer size in qsynth to its maximum value

> **Stochastic said:**
> It may also stem from some poor hardware grounding between your midi soundcard, audio soundcard, computer, and midi keyboard.  Though, if it only happens in qsynth this is probably not the case.

It doesn't happen when I'm recording my guitar with the same hardware.  The MIDI soundcard I'm using is a tascam us-122 which has both 1/4" inputs and midi, so it is the same hardware exactly.  I have not used the MIDI keyboard with any other software except Hydrogen.  In hydrogen, there is not audio playback, however.  It only programs the drum tracks.  Is there another piece of software I should use to check this?

---

### Post by Stochastic on 2009-03-21
On my old US-122 I would get strange buzzes when I paused some audio software and at other odd times.  Unfortunately, I think it may stem from the binary drivers so I just gave up and moved up to a better soundcard that was fully supported and I had been planning on buying for some time.

You may find that it's just qsynth and that an entirely different soundfont synth would not make any buzzing.  Give Fluidsynth a try.

---

### Post by le_vainqueur on 2009-03-21
Thanks for the tip.  If I chose to go with a new device, is there a list of fully supported devices I can check out?  Is there a specific device you would recommend?

---

### Post by Stochastic on 2009-03-23
I can't say from here if it's 100% the tascam's fault, try fluidsynth first to see if that's the easiest solution.  

But if you want a new device anyway, there are a few places to see if a device is supported: 
[http://www.alsaproject.org](http://www.alsaproject.org) has a listing, but it's not the easiest to look through (nor is it always up to date, or very inclusive of generic/standards compliant USB audio cards, last I checked)
[http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/) is an unofficial site that tries to only have linux supported hardware (but I notice the tascams are there too, so I guess binary drivers are considered supported).
[http://www.ffado.org/](http://www.ffado.org/) is where you should look to find out if a firewire device is supported.

I would say, if you want a new device (and want to upgrade from the US-122) a firewire device that's listed at ffado.org would be the way to go.

---

### Post by le_vainqueur on 2009-04-08
Thanks for the links. I'm shopping around on those sites right now. For my own reference, is there a specific device that you would recommend as an upgrade form the Tascam unit I have?  I want a device that I know will work properly, so I am browsing the "fully supported" devices on ffado.  They all seem to be about the same in terms of options and price range.  What does your experience tell you?

---

### Post by Stochastic on 2009-04-09
I'm working with a Presonus Firepod (now called the FP10) and am VERY happy with both it's functionality in Ubuntu (ffado is rock solid) and the sound quality.  It's listed as 'reported to work' in the ffado listings (last I checked) but this is only because Presonus has not given the ffado devs a unit on which to do any testing.

---

