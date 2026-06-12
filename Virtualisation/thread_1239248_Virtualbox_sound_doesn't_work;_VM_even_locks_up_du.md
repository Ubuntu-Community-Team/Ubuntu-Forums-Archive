---
title: "Virtualbox sound doesn't work; VM even locks up during shutdown"
date: 2009-08-13
forum: Virtualisation
---

### Post by diablo75 on 2009-08-13
I am currently using Virtualbox (non-OSE) version 2.2.4 r47978 with a Windows XP VM running, which up until the last kernel update (I think) worked with sound just fine.  Now it produces no sound.

The sound settings in the VM settings panel have it set to use the PulseAudio engine for sound.  I've also noticed that every time I try to shut the VM down via the Start Menu, or by going through the VM's Machine menu and telling to power it off, the VM will hang and require me to run xkill in ubuntu to force the window to close.

I did a little trial and error and also found that, if I set it to ALSA, it not only fails to produce sound, but completely crashes the VM and closes it's window when the VM attempts to produce sound.  If I set it to disable sound entirely, the system runs just fine with no snags, shuts down properly and all... just no sound of course.

What should I try to get this fixed?

---

### Post by diablo75 on 2009-08-14
Solved...

I hadn't realized there was a Version 3 available.  I removed 2.2.4 and installed 3, and that fixed it!

Edit:  I wanted to add that I believe the cause had to do with ALSA.  It seems that, if any other programs in Ubuntu were using ALSA to output audio things would screw up.  VLC in particular would cause such problems.  I discovered that in the case of VLC, there is a seperate vlc-plugin-pulse package that can be installed and then the output module preferences in VLC set to use Pulse Audio instead of ALSA.  Now both Virtualbox and VLC run along side each other very nicely.  I will seek out any other programs that still use ALSA and see if they can be switched to Pulse.

---

