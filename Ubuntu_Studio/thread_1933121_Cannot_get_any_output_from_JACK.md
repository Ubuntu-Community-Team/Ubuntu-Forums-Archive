---
title: "Cannot get any output from JACK"
date: 2012-02-28
forum: Ubuntu Studio
---

### Post by spearlymatt on 2012-02-28
Good afternoon everyone,

I've been experimenting with Ubuntu on various computers for about five years now, though I don't have a very technical understanding.  I have one computer I built running Ubuntu 11.04 and Vista, and a laptop running only 11.04.  Both have the studio packages on them (my first question is does 11.10 allow you to use any form of GNOME from a fresh install?  Anywhere I read online is just about installing GNOME shell.  I'm not a purist, I just tried Unity and found it very frustrating).  

A year or two ago (maybe on Ubuntu 9.10?) I had my Akai LPK25 patched through my desktop, through JACK, Qsynth, Ardour, and various effects programs with it all working beautifully.  I neglected it for awhile, and came back to find some error messages, and things weren't really working at all.  I then took the opportunity to upgrade to 11.04 (just a few days ago, and removed then installed the studio packages.  I start JACK, start QSynth, connect my keyboard to FluidSynth in the ALSA tab (as I always did before), and connect Qsynth to my output.  The light shows up on QSynth when I strike a key, but no sound.  The same goes for my laptop.  On my laptop I just connected the mic inputs to the system output and got crazy feedback, so I can get (some form of) sound.  

Any help would be greatly appreciated, I've probably just made a stupid mistake, or overlooked something along the way.  If I remember when I first set it up, it was mostly guess work on my part.  I also just burned an install DVD of Ubuntu Studio 11.04, if you think a fresh install would fix the issues.  

P.S.  Pandora won't load on my desktop's Firefox, but it will on my phone and laptop.  I've uninstalled/reinstalled firefox, and manually reinstalled Adobe (I believe a solution offered on here).  Still nothing.  It just loads with the little circle, until it times out.  Any help would also be appreciated on that problem.

---

### Post by sgx on 2012-03-01
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

links 4 and 8 at the wiki have screenshots and details that
should help set up jackd and qjackctl. The commands below
show some of how linux kernel
IDs your soundcard. In my case, snd_ice1712 is the kernel module
used for the soundchip on the maudio card, yours will be
a bit different

bash-4.1$ cat /proc/asound/cards
 0 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xac00, irq 17
bash-4.1$ cat /proc/asound/devices
  1:        : sequencer
  2: [ 0- 0]: raw midi
  3: [ 0- 0]: digital audio playback
  4: [ 0- 0]: digital audio capture
  5: [ 0]   : control
 33:        : timer

bash-4.1$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bash-4.1$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Cheers

---

### Post by spearlymatt on 2012-03-01
Thanks for the reply.  I followed the guide, and that caused my JACK to fail, saying overall system failed, server connection issues, etc.  On my laptop, that is.

---

