---
title: "Playback in Ardour 2.5 has clicks no matter what"
date: 2008-10-19
forum: Ubuntu Studio
---

### Post by thecavemaster on 2008-10-19
Hi, I run a small recording studio in northwest florida with 3 computers all running the studio flavor of 8.04. The computer I am having problems with is my attempt at being able to mix and master bands away from the studio. It is a Dell Inspiron 1501 64it. I will not be doing any capture on this machine.  The problem i am having is when i playback in ardour there is a clicking sound at a constant rhythm that that changes with my frame per period. I have tried every conceivable setup that actually allows jack to start. I do not get this clicking sound with playback in rhythmbox or audacity. I have read in the forums that this problem would go away with correct jack settings. I have thought about updating to the newest release of jack and alsa but there respected documentation does not adress any problems similar to mine. Jack Version: 0.3.2
Build: Feb 8 2008 04:48:35 
My jack settings are as follows:

 hw:0|-|4096|2|48000|0|2|nomon|swmeter|-|32bit

alsa-base 1.0.16-0ubuntu4

aplay -l :

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

  any help would be much appreciated!
If it is b/c the STAC92 can't handle multi track playback then I might purchase a used Tascam US-122 from a friend.

---

### Post by demios on 2008-10-19
I had this problem too, went through a pile of different pulse audio setup tutorials and stuff, but it turned out it was just some connection setting in Jack that I had to tweak. it was weird, and this probably doesn't help you at all, but there you go. Good luck man.

---

### Post by Stochastic on 2008-10-20
If they're regular XRuns, regularly spaced, and their spacing is dependent upon the frame size, I'd guess that there's some clocking issues.  Are you running the RT kernel on this box?  if so, try checking off the RT option in qjackctl - if you're not, then that may be the issue.

The Tascam US122 is a little tricky to setup, but if you follow a well written howto, it's not that hard.  Mine had a bit of playback noize back when I was using it in Feisty - don't know if that's been solved yet or not.

Edit: oh, and by the way that's the version# for qjackctl you've given, not jackd - do ```
apt-cache policy jackd
``` to display what version of jackd you're running (this is the proper jack version#).  It will probably be: 0.109.2-1ubuntu1

---

### Post by cb951303 on 2008-10-20
do you have xruns?

---

### Post by thecavemaster on 2008-10-20
> **cb951303 said:**
> do you have xruns?
I have xruns when jackd is on duplex or capture.I have tried every setting I could think of during capture and duplex but I have still have xruns. When I have it on playback only there are no xruns. My problem also persists with or without rt. I have also tried using the generic kernel in grub but had no change. my jackd version number is 0.109.2-1ubuntu1. I just tried ardour with the duplex setting in jackd and I could not get it to play at all!?

---

### Post by cb951303 on 2008-10-21
I tried jack with several onboard cards. Sometimes the only solution is to turn off monitoring.

---

