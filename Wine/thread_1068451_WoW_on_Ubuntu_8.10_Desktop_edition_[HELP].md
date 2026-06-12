---
title: "WoW on Ubuntu 8.10 Desktop edition [HELP]"
date: 2009-02-12
forum: Wine
---

### Post by Nakeo on 2009-02-12
Hi,

I have recently switched from windowsXP and have had alot of trouble getting WoW to run in it. I have read the tutorials on-line and only gotten information that is completely useless to me.

I have tried the WINE method but when i enter my installation disks they show up as if they were inserted into a appleOSX system one not windows so WINE wont work.

I have tried Virtual Box but i don't have any copies of windows i can permanently use (EG my keys are useless).

I have also tried Play on Linux but i still need the windows installers not the apple ones when i insert the CD's

The only way i have gotten it to run (Unusable) was at 20FPS max and now runs at 2FPS and no longer renders the graphics (I get blue triangles) it runs in 40-50 FPS with raw windows.
This was with the installed files copied from a windows system and run in WINE.

If you have any ideas thanks :)

---

### Post by Eviljim on 2009-02-13
Whether you install from the DVD or by copying from a windows version, it wont make a difference. If you are able to run the game, but get a poor fps, you need to setup the graphics driver properly.

Follow the popular howto on setting up WoW on Ubuntu.

---

### Post by Nakeo on 2009-02-14
Nah the GPU is set up properly. I was following a Tutorial about it and it said to install a windows Font Package. After installing it my FPS went from about 20 to 2. I can run WoW i just need the FPS to be about 40-60

---

### Post by hikaricore on 2009-02-14
Video hardware, drivers, etc... provide more info.
Please let us know what guides or howtos you've followed, if you have tested both opengl and d3d modes, and if you have read through all the info on the WINE application database regarding increasing framerates.

It is fully possible to copy your windows installation of WoW to your Linux partition and run it from there, installing it will make no difference.

Your best bet is to completely forget about using a virtual machine, this is just not an option.
Focus all your attention on WINE and hope for the best.

If you have an ATI or Nvidia card you have a shot at getting this working.
If you have some integrated intel "video" chipset, you're probably going to be fighting an uphill battle and will probably just want to invest in an actual video card.

---

### Post by tneva82 on 2009-02-14
> **hikaricore said:**
> If you have some integrated intel "video" chipset, you're probably going to be fighting an uphill battle and will probably just want to invest in an actual video card.

And maybe preferably nVidia. Seems their drivers are better. Albeit no personal experiences but atleast my experiences with Radeon 4870 aren't too good. Takes bit of effort to get working, need to trim graphic details for sake of FPS and there's annoying graphical glitches. Atleast from reading these forums experiences with nVidia seems to be better.

Wish I had known this when I was building my computer :(

---

### Post by Nakeo on 2009-02-24
Well as far as i know.
I have tested opengl
I have played around with the WINE settings
 And have encountered a new problem

Now when i click play in the launcher the game crashes and opens the blizzard error reporter.

Is it worth my while trying the installer off the blizz site or just continue playing with the install i have now?

---

