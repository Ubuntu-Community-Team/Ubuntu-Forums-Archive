---
title: "Is it possible to run beryl without 3D acceleration?"
date: 2007-03-01
forum: Ubuntu Customization Guide
---

### Post by prashantjois on 2007-03-01
I was looking at the Beryl docs and pretty much realized that 3D graphics card was a requirement.  I just want to test out the features though but I don't have a 3D card.  Is it still possible to run it? If so, is there a way to do through apt or synaptic (without having to compile from sources)?

Thanks,

Prashant

---

### Post by yabbadabbadont on 2007-03-01
I think that you just have to have the 3d rendering available.  It doesn't have to be hardware accelerated 3d.  Search around for information on installing and configuring the Mesa libraries.  It provides software rendered 3d.

---

### Post by bikeboy on 2007-03-01
If you don't have a 3d card, I'm guessing the rest of the specs are pretty low too (could be wrong). If that's the case, I doubt sofware 3d accel will be any good either, as it will require a very good cpu, and would most likely be slow anyway.

Just FYI though, with the right reposistories enabled, you can install Compiz through Synaptic, you just won't be getting the absolute newest releases of it. Not so sure about Beryl.

---

### Post by TheMono on 2007-03-01
Actually, it depends what your graphics adapter is. If you have Intel integrated graphics, you may well be fine.

For example - I have Beryl running on a 2 year old laptop, Intel 855GM graphics, 2.5Ghz Celeron, 512MB RAM. Runs fine.

---

### Post by bikeboy on 2007-03-01
But that integrated graphics chip is still a 3d accellerator, and a relatively decent one. I should have said you need a 3d accel chip, it doesn't have to be a separate card.

---

### Post by drtvasudevan on 2007-03-01
i have INTEL core 2 duo chipset, DG965RY mobo 1 gig RAM. running edgy 64bit.
installed beryl and when i started the bery-manager in the terminal the first time it simply hung. the second time there was some error msg and before i could make it out i was logged out.
now every time i start it i get logged out.
where do i see what happened and where do i file crash report?

---

### Post by toaste on 2007-03-01
Intel releases open source 3D drivers for their integrated graphics, and they do have 3D acceleration.  However, the 965 series chipset is brand-spanking-new, and so are the drivers for it.  What I've gathered from dealing with this myself is that Ubuntu Edgy users experience problems getting 3d to work out of the box with this chipset.

Check out _[bug 62135 in launchpad]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62135")_, there's a recompiled package for MESA that will get 3D acceleration, but unfortunately won't fix beryl.  On my system you *can* launch beryl, but nothing gets drawn in the windows (although everything does work even if I can't see it).  At least Planet Penguin Racer, bzflag, and the various 3d xscreensavers are working now.

Also, if you have an LCD panel that won't run in its native resolution, read up on the modesetting driver that Intel is still working on in _[this thread]("http://ubuntuforums.org/showthread.php?t=281275&page=10")_.  Note that the howto in the thread is not really relevant unless you compile the source code from about a month ago.  The driver is now written to compile against the more recent xserver 1.3 which should make it into the next version of Ubuntu -- 7.04 Feisty Fawn.

3D is reported to work out of the box with these chipsets under Feisty as of herd 4, including beryl.  The next pre-release snapshot, herd 5, has been slated for today, (March 1st).

---

### Post by drtvasudevan on 2007-03-02
thanks for the input.
i guess i shall have to wait.
tv

---

