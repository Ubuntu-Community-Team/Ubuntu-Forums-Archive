---
title: "Can't install Ubuntu 12.10"
date: 2012-09-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by GerbenMa on 2012-09-16
When I want to install Ubuntu 12.10 (I got this both at the beta and daily build). I get this:

---

### Post by dino99 on 2012-09-16
you might need to add nomodeset as boot option

(google about "ubuntu boot option")

---

### Post by jerrylamos on 2012-09-16
> **dino99 said:**
> you might need to add nomodeset as boot option

(google about "ubuntu boot option")I realize that Ubuntu Development is totally dedicated to "modeset" and has been since Intrepid.  I can sort of understand it for already installed Ubuntu where there there is far more video support than install.

"Install should work" is demonstrably not a priority for Ubuntu Development.  Maybe someone can explain to us why "modeset" is an essential part of Install?

I must be totally mis-informed - way back when "modeset" was touted to speed up logout-login and switching accounts maybe??  Who's doing that in Install?

Yes, I hit the modeset problem on my fast 3.3 gHz 2G pc in Quantal Alpha. I was surprised that Ubuntu Development hasn't been able to solve that yet.  I waited a couple weeks and it got fixed.

? Can anyone explain to us why Ubuntu likes to take this risk?

---

### Post by dino99 on 2012-09-16
hi Jerry,

maybe you miss a little detail: QQ is still a beta
if you pay attention to dpkg log or simply the daily upgrade list, you have surely seen than even very deep sources are "unstable" like gcc, python, and some others synced from git/upstream. So what do you expect it can be. Wait at least the first rc to ask such questions :lolflag:

---

### Post by mc4man on 2012-09-16
If you have nvidia & getting that corrupted screen nomodeset will work.
However it's also quite likely that just removing splash from the boot options will work & provide a usable live session which nomodeset doesn't

If you can't figure out how to remove splash then ask..

---

### Post by lucazade on 2012-09-16
> **jerrylamos said:**
> 
I must be totally mis-informed - way back when "modeset" was touted to speed up logout-login and switching accounts maybe??  Who's doing that in Install?


Modeset is related to video drivers and DRM kernel part of these. This feature alongside KMS allows to catch monitor native resolutions as soon as the kernel is up instead of waiting for X to startup.  
It allows a smooth boot up, without flickerings, and native resolution in VTs.

This feature unfortunately is only available with opensource drivers (radeon, nouveau and intel).

---

### Post by twipley on 2012-09-16
To install any of the latest versions of Ubuntu on my NVIDIA-card machine, here are the steps I must follow:

1) boot up from the live CD tapping the f6 key (otherwise I get a black screen with a flashing underscore);

2) press enter to select language, then press f6 again to select "nomodeset" (otherwise there will be problems);

3) after installing and rebooting, tap shift to enter grub-settings mode. When it gets there, the first (default) entry has to be selected, and that way it boots up correctly. I guess graphics drivers get installed on that first login, as afterwards the boot-up process completes without getting stuck, without having to tap any key.

---

### Post by jerrylamos on 2012-09-16
> **dino99 said:**
> hi Jerry, maybe you miss a little detail: QQ is still a betaYes, it's a Beta, that's why we are on this forum.  I've been doing Beta's since Dapper Drake.  For that matter, I was working at IBM testing when the terms Alpha and Beta were first defined.  Over several years I've been battered by "modeset" so that's a sore point.  

Ubuntu expects users to experiment with F6 maybe Ubuntu could do some more bullet proofing on install image booting.  I'm not volunteering I'm not a developer, just a user.  Minority opinion, if I did do anything with install I'd ditch modeset and other features which are not necessary to get the install booted.

---

### Post by twipley on 2012-09-16
> **jerrylamos said:**
> Ubuntu expects users to experiment with F6 maybe Ubuntu could do some more bullet proofing on install image booting.  I'm not volunteering I'm not a developer, just a user.  Minority opinion, if I did do anything with install I'd ditch modeset and other features which are not necessary to get the install booted.
I do not want to sound complaining either, although I am left wondering, having experienced this, how many users are turned off by a Ubuntu that cannot install on their system -- without more-or-less-documented workarounds, that is, such as following the steps I posted above, or using the alternate installer (edit: if even the latter is a thorough solution).

---

### Post by jay87 on 2012-10-18
I can't download Ubuntu 12.10 yet in the UK.   Anyone know what time it's expected to go live?

Thanks

---

### Post by randomizer101 on 2012-10-18
> **jay87 said:**
> I can't download Ubuntu 12.10 yet in the UK.   Anyone know what time it's expected to go live?

Thanks

The source ISOs are up so presumably in the next few hours, although potentially a bit longer before the "official" release.

---

### Post by Cheesemill on 2012-10-18
When it's ready.

It will be at some point today.

---

### Post by dakshbhatt21 on 2012-10-18
I am also waiting hardly for it . . .:confused:

---

### Post by TREESofRIGHTEOUSNESS on 2012-10-18
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by Jæd on 2012-10-18
> **TREESofRIGHTEOUSNESS said:**
> [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

That gives "Ubuntu 12.10 (Quantal Quetzal) Beta 2"

---

### Post by kansasnoob on 2012-10-18
You can see from the QA Tracker that not quite all of the images are ready:

[http://iso.qa.ubuntu.com/qatracker/milestones/240/builds](http://iso.qa.ubuntu.com/qatracker/milestones/240/builds)

You can also be sure that each flavors QA team is putting the final touches on the release notes :)

---

