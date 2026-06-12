---
title: "Ubuntu 12 Studio - SSD optimization."
date: 2012-06-01
forum: Ubuntu Studio
---

### Post by DJonsson2008 on 2012-06-01
Intel(R) Atom(TM) CPU  330   @ 1.60GHz
2GB Ram


I just loaded Studio 12 onto an Intel 40GB Sata II SSD.

* Do I need to optimize the install for SSD?

* Would placing my directories that get the bulk of
  read writes during recording onto another drive 
  be a good idea?

I used the machine mostly for recording jam sessions.

Please advise

---

### Post by Sylos on 2012-09-08
Well that was off topic!


Anyhow, to the OP - conventional wisdom is that you need to enabled TRIM (support is included in the kernel but needs to be turned on). This will keep the writes to the disk reasonably even across it (I think).

Its also common for people to keep their home directory on the SSD (all your configs are here so having it on a slower drive would put a dent in your speed gain from the SSD) BUT have all your data on a normal HDD (eg. movies, downloads, stuff you record).

Thats my thoughts on the matter.

For TRIM read here:[http://ubuntuforums.org/showthread.php?t=1974320](http://ubuntuforums.org/showthread.php?t=1974320)

Cheers

---

