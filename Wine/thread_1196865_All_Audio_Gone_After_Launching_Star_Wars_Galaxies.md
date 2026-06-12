---
title: "All Audio Gone After Launching Star Wars Galaxies"
date: 2009-06-25
forum: Wine
---

### Post by Malvolio on 2009-06-25
Recently I went back to Star Wars Galaxies and, in the middle of a quest, the game hard-crashed forcing me to reboot my system.  Now, when the game proper launches it kills my sound.  Before this the sound is fine, even in Wine.  The launcher makes it's sounds, ALSA sound test works, I can even play music with Audacious.  After, I can't even play music in Audacious.  I've tried wineprefixcreate and changing audio between OSS and ALSA in Wine but nothing seems to work once Star Wars Galaxies proper is launched.  When I close the game sound tends to return.  I'm sure the game is at fault but I'm not sure how.  I've tried running Starcraft in Wine and it still has sound so I know it's not Wine.

Append: Well, tried having Audacious running when Star Wars Galaxies launches and that seems to have worked, but it's a band-aid.  I still need a proper fix.

Another Append: Seems Star Wars Galaxies may well be on the way to Bronze rating.  Tried playing it several more times under varying conditions and it will invariably crash.  A shame.

---

### Post by lvlo on 2009-06-25
Try to set OSS audio output, "Emulation" in "Hardware Acceleration" box and check in "Driver Emulation" checkbox. Helped me with Live For Speed game, but my problem was that LFS just muted master volume channel in sound mixer.

---

### Post by NightMKoder on 2009-06-25
pulseaudio is evil. Start your games with pasuspender:

pasuspender wine starwars.exe

or whatever the file is called. pasuspender is in pulseaudio-utils.

---

### Post by Malvolio on 2009-07-05
Thanks for the replies, though I think I found the culprit.  Turns out it was the hard drive... got a new one, reinstalling now to see if that was indeed it.  Who knew, right?  My friend poked fun at me, he's never had a hard drive failure yet this is my... second one?  It's so funny it hurts.

Append: Fresh install, sound still didn't work in ALSA.  Switched to OSS and the sound worked fine.  Graphics are wonky.  They work for a while though my screen 'blinks' occasionally, but after a few blinks the faces of the 'human' races become garbled and my desktop a mess of blank streaks.  Can't help but think something was changed in a recent SWG patches, but there's got to be a fix for it.

I'm using an NVidia Geforce Go on a Dell E1505.  The restricted drivers are enabled.

Another Append: Okay, the problem was PulseAudio the whole time as far as sound went.  Installed Ubuntu 9.04 and it solved alot of sound issues.  Haven't run into the graphics glitch yet so I'm holding out hope that that was transitory.

---

