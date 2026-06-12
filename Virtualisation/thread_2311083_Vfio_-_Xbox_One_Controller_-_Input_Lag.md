---
title: "Vfio - Xbox One Controller - Input Lag??"
date: 2016-01-24
forum: Virtualisation
---

### Post by KillerKelvUK on 2016-01-24
Have a Windows 10 kvm/qemu guest using vfio and an old nVidia GTX 650..works a treat 100% for business type use and 95% of the time for games use. 5% of the time I get horrendous input lag from my X1 controller but keyboard/mouse seems unaffected.  I know my GFX hardware is old so not expecting the world from that, my test cases so far have been the Crysis series where I've had the same problem against Crysis, Crysis Warhead and now Crysis 2 (Crysis 3 up next).  The lag is short lived (~10 to 15 seconds) and then returns to normal and like I mention during the X1 lag my keyboard/mouse movements seem fine.  I have noticed the lag seems to occur during high action game segments where game FPS will be low as the CPU & GFX are doing a lot, however I can't explain why the mouse movements are unaffected at these same times?

Has anyone else got a comparable?  Can anyone point me in a direction to debug if this is potentially a host-to-guest issue?  General advice welcome...I've no log message worth sharing that I can discern, no error messages save the occasional nVidia driver crash which is unrelated IMO.

---

### Post by KillerKelvUK on 2016-01-31
Solved by upgrading the ancient gfx card :-)

---

