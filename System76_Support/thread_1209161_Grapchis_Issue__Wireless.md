---
title: "Grapchis Issue / Wireless"
date: 2009-07-10
forum: System76 Support
---

### Post by Vrekk on 2009-07-10
Ok i got my Netbook today and i reinstalled Ubuntu as described [here]("http://ubuntuforums.org/showthread.php?t=1205242"), but now im having some very werid issues.  After installing UNR, I get a very strange issue when on the Ubuntu Netbook desktop (not the classic).  The panles are gone and when i open a windows it with randomly disapper and reapper.  Im also having the issue with Signal strength and connecting wireless.  Any help would be nice :D.

(Btw i did install the System 76 drivers)

---

### Post by Vrekk on 2009-07-10
Ok i was able to solve the graphics issue by running
```
sudo apt-get remove gnome-panels && sudo apt-get install gnome-panels
sudo apt-get install ubuntu-netbook-remix
```

The code only took about a minute to run and now that is working fine.  Im stilling having that wireless issue, but i noticed that it sounds like a general issue with the Starling.

---

### Post by jml on 2009-07-10
You are right.  The Starling has a well documented issue with wireless.  According to Tom, the S76 representative on this forum, it is a driver issue.  S76 is working on it.  Right now, it seems that the only solution is to get as physically close to the wireless access point as possible.  The Starling seems to connect reliably in that setting.  Not an ideal solution, but one that works.

Joe

---

