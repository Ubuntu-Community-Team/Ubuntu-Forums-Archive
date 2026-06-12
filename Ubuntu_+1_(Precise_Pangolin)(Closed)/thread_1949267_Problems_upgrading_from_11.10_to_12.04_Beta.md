---
title: "Problems upgrading from 11.10 to 12.04 Beta"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by andrewrichardson4 on 2012-03-29
Good evening! I'm not sure if I've found the right place to pose this question, but I'm having difficulties upgrading to Ubuntu 12.04 Beta due to a problem with the dependency cycle. I took a screenshot of the error and have attached it. I would be very grateful if I could get some help working through this. Thank you!

---

### Post by Bucky Ball on 2012-03-29
12.04 LTS is unreleased and beta. Expect breakages, bugs and glitches.

 I have asked mods to move this post to the appropriate forum. ;)

---

### Post by drs305 on 2012-03-29
Moved to Ubuntu+1

---

### Post by critin on 2012-03-29
I hasn't been released for upgrading yet.  If you want to run it, you'll need to download the iso and install.

---

### Post by grahammechanical on 2012-03-29
Please go to this link and look for the heading Upgrades.

You will find this written there:

> In some cases, the package manager in Ubuntu 11.10 may not be able to  decide on a correct unpack ordering when upgrading 64-bit systems with  the ia32-libs package installed; if this is  the case, it will fail before starting to unpack any new packages with a  message something like "Couldn't configure pre-depend libtinfo5 for  libncurses5, probably a dependency cycle".  A workaround is to install  the apt and libapt-pkg4.12 packages from precise before starting the upgrade. ([924079]("https://bugs.launchpad.net/bugs/924079")) 

[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Checking_the_Desktop_Default_Applications](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Checking_the_Desktop_Default_Applications)

Regards

---

### Post by kansasnoob on 2012-03-30
> **andrewrichardson4 said:**
> Good evening! I'm not sure if I've found the right place to pose this question, but I'm having difficulties upgrading to Ubuntu 12.04 Beta due to a problem with the dependency cycle. I took a screenshot of the error and have attached it. I would be very grateful if I could get some help working through this. Thank you!

That's this bug:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/924079](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/924079)

The work-around is in comment #23.

---

### Post by andrewrichardson4 on 2012-03-30
Thank you all so much for your help. I'll implement the suggestions here and post the results this afternoon.

---

