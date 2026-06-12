---
title: "Convergence one year after Ubuntu Edge"
date: 2014-07-13
forum: The Cafe
---

### Post by lads on 2014-07-13
One year has passed since the Ubuntu Edge experiment. Since then it seems not much has happened regarding the general concept of *Converge*. 

What are you thoughts? How far are we from handsets capable of providing both an hand/touch experience and a full desktop interface? And which OS family will make it first? Microsoft, Apple or Linux?

---

### Post by ian-weisser on 2014-07-13
Well, perhaps you haven't been participating in the Ubuntu Online Summits or reading the Ubuntu-developers e-mail list, or seeing the press releases.

1) Last [story I saw]("http://www.cnet.com/news/ubuntu-touch-gets-grip-on-its-first-phone-makers/") two handset makers were preparing to develop Ubuntu handsets "in 2014". We have all seen vaporware before, and it's debatable if the software will be ready...but even the expressed interest is a big improvement over the past.

2) The most recent [online summit]("http://summit.ubuntu.com/uos-1406/") included detail on huge amounts of completed work on convergence, and lots of technical discussion on what more needs to be done.
- Mir is coming along nicely (phones can't use X well)
- The converged version of Unity (Unity 8) is coming along nicely and the basic set of phone-style apps for it are mostly complete
- The shift from Upstart and GTK to systemd and QT are in progress. A few rather thorny issues to iron out with the migrations, but nothing impossible
- The SDK has been revamped and a phone-emulator created so developers can create apps
- The problems with using apt in a memory-limited and bandwidth-limited phone environment are being investigated, a few solutions have been suggested.

---

### Post by grahammechanical on 2014-07-13
The Ubuntu developers have set the end of August this year as the latest by which Ubuntu for phones and tablets is RTM (Release To Manufacture). Which I take to mean in a suitable state for OEMs to install it on their hardware for retail.

We also now have Ubuntu-Desktop-Next ISO images for testing. Instead of bringing all the convergence code into the development branches of 14.10, 15.04 and 15.10 and risk causing those releases to be unstable, we have a parallel code track that is built on the Utopic Unicorn code base but also has Mir, Unity 8 and the phone/tablet apps.

Ubuntu-Desktop-Next is very new. It still uses Xserver and LightDM to get to a login screen and unless you have Intel graphics it won't go much further than the login screen without freezing the OS. That is the sate it is in on my machine with an Nvidia GT220 running Nouveau. Here are a couple of threads on this subject

[http://ubuntuforums.org/showthread.php?t=2229306](http://ubuntuforums.org/showthread.php?t=2229306)

[http://ubuntuforums.org/showthread.php?t=2228993](http://ubuntuforums.org/showthread.php?t=2228993)

The problems with the installer have been fixed.

Regards.

---

### Post by lads on 2014-07-14
Thank you for the replies. I am sorry but I do not seem to have made myself clear. I have been following the developments towards *Convergence* with Ubuntu: Mir, Unity 8, etc. I am also aware that Windows 9 is going the  same direct. Now my question really is on the hardware. Anything like the Ubuntu Edge on the works that we can expect to come to fruition? Any guesses on when it will be user ready?

Thanks for sharing your insights.

---

