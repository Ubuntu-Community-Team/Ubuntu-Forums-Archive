---
title: "Flash Trouble in Precise Pangolin"
date: 2011-12-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jdogzz on 2011-12-19
I recently installed the most recent version of 12.04 to my computer and so far there have been only a few glitches that I've been able to work around, such as installing things without the software center. The only thing that I haven't been able to get to work is flash player. It doesn't work in Mozilla Firefox, the nightly version, Google Chrome, and Chromium Daily (I did try all of them). I have tried removing it and reinstalling it, downloading the package from off the adobe website and manually placing it into the proper area, and nothing has worked. Has anyone here had this problem and fixed it, or know a way I might be able to fix it?

Edit: Flash seems to be working in the firefoxes now. Chromium Daily still seems to be malfunctioning though. Similar problem is here: [http://ubuntuforums.org/showthread.php?t=1897434](http://ubuntuforums.org/showthread.php?t=1897434)

---

### Post by cariboo on 2011-12-19
Move to Precise Testing & Discussion.

---

### Post by Jdogzz on 2011-12-19
Thanks for moving it:) I didn't know if it was supposed to go in this section because it said "Discussion" and not bugs:)

Hopefully someone can point out a solution.

---

### Post by Harry33 on 2011-12-20
I have several different setups (64-bit, 32-bit, Nvidia, Intel, AMD).
Flash is working fine here both with Chromium and Firefox.

---

### Post by VinDSL on 2011-12-20
> **Jdogzz said:**
> Hopefully someone can point out a solution.
Make sure the Flash plug-in is installed / enabled in Chromium...


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-20-dec-2011-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-20-dec-2011-1.png")[/INDENT]


That's the only problem I've had with Flash in Chromium / Google Chrome.

---

### Post by paul_in_london on 2011-12-20
> **Jdogzz said:**
> I recently installed the most recent version of 12.04 to my computer and so far there have been only a few glitches that I've been able to work around, such as installing things without the software center. The only thing that I haven't been able to get to work is flash player. It doesn't work in Mozilla Firefox, the nightly version, Google Chrome, and Chromium Daily (I did try all of them). I have tried removing it and reinstalling it, downloading the package from off the adobe website and manually placing it into the proper area, and nothing has worked. Has anyone here had this problem and fixed it, or know a way I might be able to fix it?

Edit: Flash seems to be working in the firefoxes now. Chromium Daily still seems to be malfunctioning though. Similar problem is here: [http://ubuntuforums.org/showthread.php?t=1897434](http://ubuntuforums.org/showthread.php?t=1897434)

Flash was still ok for me in FF daily 64 bit after last night's updates. google chrome **17.0.963.12 dev** 64 bit was also still ok, but chromium-daily 64 bit now seems to be failing to
detect plugins (didn't test 32 bit). I found a recent bug report from a quick search yesterday relating to this, but haven't hunted around any further yet:

[http://code.google.com/p/chromium/issues/detail?id=107955](http://code.google.com/p/chromium/issues/detail?id=107955)

---

