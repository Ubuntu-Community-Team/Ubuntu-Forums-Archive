---
title: "nvidia-driver on 1910 install not the recommended driver"
date: 2019-10-14
forum: Ubuntu Development Version
---

### Post by bobbicat on 2019-10-14
Maybe this is something that will be fixed in the release candidate.

I now have kubuntu1910 on my computer after running 'sudo do-release-upgrade -d' in kubuntu1904.
The upgrade appeared to progress flawlessly, though this is not the release candidate. 

However, I was looking at the drivers for my PC and noticed that nvideo-driver-430 had been installed, even though in the list -435 was the recommended driver.
Trying to switch to the recommended driver appeared to be impossible.

So, after reading around, I tried purging driver-430, rebooting and then installing driver-435.
I was successful in this but a file libnvidia-compute-430:amd64 still remained, I purged this and as far as I can see all is now well.

I would report this as a bug but the intricacy of doing so held me back, I post it here in the hope that it will be noticed. 
This is not a request for help, just a note to point out that during a do-release-upgrade the installation of nvidia driver is not progressing as it should.

If more info about my system and/or method would help then just ask.

---

