---
title: "Why is fglrx stuck at 11.11 ?"
date: 2012-02-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rajeev1204 on 2012-02-22
The version i have is at 11.11, and newer releases have come in after that. ANy particular reason newer packages havent been built yet?

---

### Post by sonicb00m on 2012-02-22
I think AMD has to build it for the right version of Xserver. I couldn't get newer versions of the binary to work installing manually.

As anyone ever had any success installing the "post release" update in the restricted driver manager? This has never worked for me since it was introduced in the previous Ubuntu.

---

### Post by jfernyhough on 2012-02-22
What are you using to check the version? IIRC amdcccle reports the first version that was installed (unless that bug has been fixed).

It's easy enough to build and install from the AMD download, though: [http://ubuntuforums.org/showthread.php?t=1915488](http://ubuntuforums.org/showthread.php?t=1915488)

---

### Post by rajeev1204 on 2012-02-22
> **jfernyhough said:**
> What are you using to check the version? IIRC amdcccle reports the first version that was installed (unless that bug has been fixed).

It's easy enough to build and install from the AMD download, though: [http://ubuntuforums.org/showthread.php?t=1915488](http://ubuntuforums.org/showthread.php?t=1915488)

The package in synaptic has these details :

fglrx-installer-updates (2:8.911-0ubuntu1) precise; urgency=low

  * New upstream release (11-11)
I checked the launchpad page and it is at this version. Havent seen fglrx not being updated for an alpha version before. 11.11 is like 4 months old.

---

