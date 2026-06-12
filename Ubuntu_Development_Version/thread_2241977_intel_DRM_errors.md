---
title: "intel DRM errors"
date: 2014-08-29
forum: Ubuntu Development Version
---

### Post by nomenkultur on 2014-08-29
Has there been any change with the intel drivers this past week?

 Was using a daily iso from a week or so ago, 10/11 days, and didn't have any errors and now after post before the splash screen with the dots I get some strange error pertaining to something something Intel DRM error failed something

---

### Post by JMB74 on 2014-08-30
Yes, there have been updates to mesa, libdrm and the kernel, hence the intel and generic parts of the graphics stacks in those.

---

### Post by fjgaude on 2014-08-30
No issues with the last update, Beta 1, with my Intel HD4600 setup, i5-4670K, Z87.

---

### Post by nomenkultur on 2014-09-03
drm:init ring common ERROR render ring initialization failed
001f001 head001131c tail00000 start 

 drm:i915 gem init ERROR failed to initialize gpu, declar .... wedged



 intel gen4 GM45 on a thinkpad.... please look into this as ubuntu 12.10 was unusable due to a intel drm error

---

### Post by jerrylamos on 2014-09-03
May be related - I've been getting compiz hence unity failures on 3.16.0-7, 8, 9, 10, 11.  3.16.  From multiple launchpad bug comments, something in the kernel causes the intel driver/compiz to fail, keeping the same ubuntu using a different kernel may run.  Latest .iso today is still at 3.16.0-11 which I boot by adding nomodeset to the linux line on the grub boot display.  Runs with lousy low resolution graphics.  Then do sudo apt-get update and sudo apt-get dist-upgrade.  The resulting 3.16.0-12 will then run O.K. on my and a couple other people's pc's.  Some still fail....

---

### Post by nomenkultur on 2014-09-08
I think it's the fact that they're still using old mesa version (???)  I don't know ... but intel drivers not working is dropping the ball big time since they have to OTB every time .... I hope 12.10 was just a freak accident

---

### Post by JMB74 on 2014-09-08
If I had to guess with that error message I would think perhaps the kernel at first, especially as it's occurring at that stage in boot/startup.

Running the daily ISO is almost inevitable you are going to run up against something like this eventually. Gen4 is also quite old.

The intel driver stack is well and rapidly maintained compared to some to be honest. I've reported and had solved several bugs, with the devs very quick to respond and track down problems.

It is worth reporting a bug to upstream and posting on mailing lists.

---

