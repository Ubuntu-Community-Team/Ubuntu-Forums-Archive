---
title: "[SOLVED] kernel update - Low graphics mode"
date: 2008-07-16
forum: System76 Support
---

### Post by kbuel on 2008-07-16
I have a pangolin performance laptop.  I just did an update and the Kernel updated from  2.6.24-17 to 2.6.24-19, and after I restarted, the computer can't load X and goes into low graphics mode.  Is this a known issue?

---

### Post by thomasaaron on 2008-07-17
That's the first time I've seen that happen in a while.

Try running your system76 driver and rebooting...

System > Administration > System76 Driver > Install Tab > Install Button.

---

### Post by MorphWVUtuba on 2008-07-17
I had a similar problem on my non-S76 desktop, which has an NVidia graphics card.  If I boot the "dash19" kernel, I lose Compiz-Fusion.  I'll just stay on the 2.6.24-16-generic until NVidia chooses to fix their binary crap or I get fed up and go buy an ATI card from somewhere.:mad:

---

### Post by kbuel on 2008-07-17
I reinstalled the system 76 driver and it still goes into low graphics mode.

This computer uses an nvidia graphics card too.  It is using the nvidia-glx-new driver.

I tried reinstalling this driver but still no luck.

---

### Post by FTBPrimeEvil on 2008-07-18
I have no idea what a system 76 is, but all you need to do is re-instate your backup file of your xorg.conf

or do a "cat' on all the files called xorg.* etc...... to find the right one with the correct parameters

Usually Located at /etc/X11

When you install the nvidia drivers it over rights the xorg.conf file. but i noticed that if you re-install the nvidia drivers a second time due to a kernel update the xorg.conf file is not over right'n like it should be, thus causing problems.

among other files the xorg.conf is one that i keep a backup of.

---

### Post by thomasaaron on 2008-07-18
Please do this:

```
sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig
sudo reboot now
```

---

### Post by kbuel on 2008-07-18
Hi,

I ran those three commands but when it restarted it is still goes into low graphics mode.

---

### Post by thomasaaron on 2008-07-18
Hmmm...

That's kind of odd. I just did that test on your configuration in the shop, and it worked. So, you must have something else hosing nvidia. Maybe...

Have you tried setting your resolution? System > Prefs > Screen Resolution?
(Sorry, I have to ask...)

---

### Post by kbuel on 2008-07-18
Yeah when I try to set the screen resolution the highest is 800x600.

Also under hardware drivers it doesn't list nvidia. (which may be normal, when in low graphics mode)

---

### Post by kbuel on 2008-07-18
I'm trying to think what I would have done to hurt the original set up.  The only "crazy" thing I can think of was installing trying to configure... and then uninstalling kppp.

---

### Post by kbuel on 2008-07-20
When I went to the System 76 driver and went to the system info tab, it said that this was a "serval performance" but my laptop is actually a Pangolin performance.

I was thinking that maybe my laptop was not imaged correctly?

Because I really didn't do anything except for just run the ubuntu update/upgrade, I didn't have anything to lose, so i just formatted it and re-installed Ubuntu.

I have now done a normal apt-get update/upgrade and everything is working... (not in low graphics mode)

---

### Post by thomasaaron on 2008-07-21
That is just a bug in the driver, where it doesn't properly recognize your particular model. That does not affect the nvidia, though. Sounds like you just had a badly hosed configuration somewhere.

---

