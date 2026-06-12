---
title: "Ubuntu Studio 12.04 - What happened?"
date: 2012-04-28
forum: Ubuntu Studio
---

### Post by deusdiabolus on 2012-04-28
I have a stock Dell Dimension 4600 ([http://support.dell.com/support/edocs/systems/dim4600/en/4600/sm/specs.htm](http://support.dell.com/support/edocs/systems/dim4600/en/4600/sm/specs.htm)) with 1GB with an AMD video card.  I did a fresh install of Studio 12.04 from a USB drive.  Everything seemed to be okay...until I started configuring things.

1.  Firefox was extremely slow and sluggish, even before I synced it.

2.  I loaded Audacious and tried to play an MP3.  It stuttered the first second and then there was no sound at all, regardless of what sound server I chose.  I tried a FLAC and got the same result.  I installed Rhythmbox and got the same result.

3.  I loaded Totem Movie Player and tried to play several videos (FLV, AVI, MPG, WMV).  They all froze after the first second.  Attempting to play back in Xine seemed to be working at first, but when I tried to seek search, the video froze and there was no further response.

4.  I decided to try and load the proprietary AMD drivers to see if it would help with anything.  Upon rebooting, I was able to get as far as the login screen, and then the OS froze while loading.  I tried deleting xorg.conf in recovery mode and making sure aticonfig --initial was run, but I got the same exact result after rebooting.

I went through the first four or five pages of threads here in an attempt to figure out what was going on and see if anyone else had the same problem.  I don't know what else to do at this point, but I thought I would at least tell you what happened with me.

One of these days I'll be able to afford to build a new machine and maybe I will stop having these horrific experiences EVERY TIME THERE'S AN UBUNTU UPGRADE.

---

### Post by cub on 2012-04-29
I have no ideas on your issues. However, is there something you need that is available in 12.04 and not in the previous installation? Otherwise, as boring as it may sound, reinstall the last version if you were happy with it?

---

### Post by sgx on 2012-04-29
The best thing is to just wait a couple months when
a new release comes out, and let developers sort through
the issues that crop up.
Use a spare drive, usbstick-install or live-dvd to try new things,
so you can contribute to testing, while still enjoying a stable
system.

I doubt it's humanly possible to do enough pre-release testing,
as the peanut gallery would froth at the mouth over the delay.
So a compromise must be accepted.
Cheers

---

### Post by sgx on 2012-04-29
You might want to try Bodhi linux, based on ubuntu, but without
the bloat, the .iso is 400 or so meg, and works fine as a live cd.

This will let you see a top-notch alternative at work, and you can
note the various versions used.

[http://www.bodhilinux.com/](http://www.bodhilinux.com/) 

Check out the 'desktop of the week' slideshow!

---

### Post by deusdiabolus on 2012-04-30
I ended up installing Pinguy 11.04 instead.  I still had to boot it in recovery mode and download a bunch of updates for it to work, but it's pretty much functioning.  

I'm still having this occasional issue with certain actions causing the OS to freeze and then the screen blinks off and on two or three times....I can't remember what the fix was, but I know I've had that problem before.

---

### Post by marty777 on 2012-06-15
[COLOR=black][FONT=Tahoma]If you still get occasional OS freeze or random logout or other curious things (for example: Firefox ALWAYS crashes on startup - even after uninstall and new installation), it is a good idea to check kernel.log. I had the same and finally I have found serious HDD errors, that did not show up in /var/log/messages.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]I had to change the disk drive. I did a fresh 12.04 Install (and did not upgrade my old and corrupted 8.04-11.10 installation). Now everything runs smoothly.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][COLOR=black][FONT=Tahoma]I hope this helps.[/FONT][/COLOR][/FONT][/COLOR]

---

