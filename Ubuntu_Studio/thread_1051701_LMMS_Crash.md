---
title: "LMMS Crash"
date: 2009-01-26
forum: Ubuntu Studio
---

### Post by jsilas on 2009-01-26
I'm having the same issue with LMMS. Only when it crashes, this is whats in the terminal. I'm using Ubuntu 8.10 64bit

---

### Post by jsilas on 2009-01-26
sorry, this is what it reads



could not set realtime priority. (as the program starts up)
Segmentation fault               (when the program crashes)

---

### Post by Stochastic on 2009-01-27
Moved your posts to their own thread, as you're using a totally different LMMS version and getting a totally different error than the original thread you dug up.

As for your error, it looks like LMMS requires (or is set to use) realtime scheduling.  You may need to install the linux-rt package, but the RT kernel in Intrepid is somewhat broken (only uses one core of multi-core processors, and doesn't shutdown unless network manager is manually killed).  You may just be able to get it running if jack is running first.

I'm on a 32-bit intrepid install and am unable to reproduce your error.  I get a clean, but strange acting LMMS - no error.

You may want to try downloading a newer version of LMMS as the repository version is slightly old.

---

### Post by simtaalo on 2009-01-27
the repo version is VERY old, you need to get ver 0.4.2

go to this page for info 
[https://launchpad.net/~tobydox/+archive](https://launchpad.net/~tobydox/+archive)

add

```
deb http://ppa.launchpad.net/tobydox/ubuntu intrepid main
```

to your etc/apt/sources.list

obviously uninstall your old version, run ```
sudo apt-get update
``` then install lmms and things should be alot more stable.

---

