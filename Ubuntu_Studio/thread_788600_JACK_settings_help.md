---
title: "JACK settings help"
date: 2008-05-09
forum: Ubuntu Studio
---

### Post by Pocadotty on 2008-05-09
here is my system...
Dell inspiron 1420n (the ones made for ubuntu)
OS: UbuntuStudio 8.04 on rt kernel (64 bit version)
CPU: intel core 2 duo (T5450 @ 1.66G
Integrated intel HD Audio

The problem I have been getting is that no matter what setting I have JACK configured with, I get a massive amount of x-runs. Even running at 44.1k with 1024 frames/period (latency of 46.4ms).  It is an HD card so I should be able to run at 96k at 24 bit depth, with fewer frames per period.

One thing that caught my eye is the wait time in jack setup is set at 21333 microseconds, which seams quite long (21.333ms), but there is no way to change this.

Can anyone give me some ideas to get JACK working properly, this will be my main studio machine, so I have to get it fixed.

I do plan on buying a pro-level sound card for it, but that is a couple months out.

Any  ideas welcome...

Thanks

---

### Post by Steveway on 2008-05-09
You should consider using a real-time-kernel.
You can install one through the usual way.
If you got that running then you can set jack to real-time-mode.
That will greatly reduce x-runs.

---

### Post by robeast on 2008-05-10
Have you properly prepared an audio group and given it the proper real time access and permissions as outlined in the link below?
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Even though Hardy has the Ubuntu Studio Control utility that takes care of this I still had to create the audio group, make myself a part of it, and my memlock limit to unlimited in /etc/security/limits.conf. I was getting choppy audio and some xruns before doing that and now I have much better performance and no xruns.

---

### Post by thirdspace on 2008-05-10
Other things to try (either or both): 
  set periods/buffer to 4 (perhaps also reduce samples/period)
  set sample rate to 48000

There seem to be a lot of versions of Intel HD audio, but these help for some of them.

---

### Post by Pocadotty on 2008-05-11
Thanks thirdspace setting the periods/buffer to 4 did the trick. Except I am running at 96kHz without a problem, likely cause it is an HD card... does anyone know if I can change the word length to 24?

Oh, and I am running the real-time kernel

---

### Post by Stochastic on 2008-05-11
The word length should be as large as the card is attempting to work with unless in jack's settings you've turned on the "force 16-bit" setting.  So yeah 24-bits is what it's running at if that's what your card can do.

---

