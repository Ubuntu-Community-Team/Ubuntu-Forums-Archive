---
title: "Presonus FP10, Digidesign mBox2 Mini and Alesis Multimix 16 firewire"
date: 2009-02-25
forum: Ubuntu Studio
---

### Post by jackliveshere on 2009-02-25
Hi all, I have two sound devices I am trying to use with Ubuntu Studio. The first is a 8 Track Presonus FP10 (formerly firepod) and the second is a Digidesign mBox2 Mini. 
I tried activating freebob in JackControl and setting the driver type to Ffado in Ardour, but none of these seem to even recognise the device (that's for the fp10).
As for the mbox, the system actually "sees" the device (which is kinda weird seeing the USB LED doesn't even light on the box.
Oh, and I have a friend who has an Alesis Multimix 16 Firewire, and he can't get it to work either (no system recognition, tried with freebob).
Please bear in mind that my friend and I are both more or less noobs and anything that doesn't have a graphical interface tends to frighten us(:p), but we'd really appreciate your help.

---

### Post by Stochastic on 2009-02-25
Yes, firewire access is limited to root by default as the spec gives direct access to system RAM - which some security guys really don't like.  If all you're using firewire for is audio, then there's no reason to leave this like this IMHO - but the default setting is not going to change anytime soon.

To work around this, do ```
sudo apt-get install ubuntustudio-controls
```
Then go into System->Administration->UbuntuStudio Controls
There, check all three checkboxes, set the memlock to about 85% or so, and set the nice value to about -10, click apply, and close.

I'm not sure if a reboot is required, but it's a good idea to force all the new settings into being.

Then Jack should be able to access the firepod and multimix.  If you get any further errors, please post them.

Unfortunately I have no idea how to get an mBox working in Ubuntu - but if you have an FP10, then I see no reason why would you want an mBox to work (they sound much worse).

---

### Post by kayosiii on 2009-02-26
also by default the FP10 works with the freebob driver but not the firewire driver... see if somebody has packaged libffado for your version of Ubuntu if you want to use the firewire driver.

---

### Post by cggaret on 2009-02-28
I've gotten my Multimix Firewire working.  Go to the FFADO subversion site [http://subversion.ffado.org/]("http://subversion.ffado.org/") and follow their directions for installing ffado and reinstalling jackd.  This does require a lot of command line stuff, but their directions are clear and concise.  To get the Multimix going you must get the latest version from svn and set ENABLE_DICE=True when compiling with scons.  There is currently no graphical way to do this since Alesis refuses to admit that Linux exists and FFADO can't support devices whose vendors don't care, but it works.  Not only does it work, it works way better than it ever did on Windows.  The official Alesis drivers were always a bit buggy for me.  Hope this helps.  I know nothing of the FP10 and mBox2, but the FP10 is reported to work with FFADO.  Good luck.

---

