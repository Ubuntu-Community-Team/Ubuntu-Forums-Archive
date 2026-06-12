---
title: "installing applications in live usb 12.04"
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zhanglini on 2012-03-17
Hi, I am currently using 10.04 32-bits, and waiting for 12.04 (64 bits this time) final version in April.
So I installed 12.04 beta onto a usb (live and persistent), to see if everything would work fine.  Most things worked, but I just could not install applications --- Skype, Wine etc.
This makes me wonder, does persist ency mean ONLY your settings can be changed, or you can modify anything within the installation?
Thanks in advance!

---

### Post by howefield on 2012-03-17
Thread moved to the "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by keithpeter on 2012-03-17
Hello zhanglini

What happens when you try to install software?

I've just booted my PC off a 4Gb usb stick with live Precise image, and about 2Gb of persistent storage, so a little less than the maximum the slider showed in Start Up Disk creator.

I'm installing Audacity. Tried from Ubuntu Software Centre, but that is a bit crashy at present so gave up. Audacity is in Universe so had to add that repository to the software sources. Had to use apt-get update (but not upgrade) to refresh software sources, then installed using apt-get install audacity. Seems to be installing OK now.

---

### Post by zhanglini on 2012-03-17
Thanks Keith, when I tried to install Skype, it said I needed "aptitude", then when I tried to install aptitude, it had some other dependency issues.  From what you were saying, one should be able to install new softwares to a persistent live usb.
I have since decided to partition my harddrive a bit, and do a dual install --- it's probably a better way of checking out 12.04 and should be faster anyway.
Thanks

---

### Post by zhanglini on 2012-03-17
Howe, although I mentioned 12.04, the issue itself is not necessarily 12.04 specific.
Thanks

---

