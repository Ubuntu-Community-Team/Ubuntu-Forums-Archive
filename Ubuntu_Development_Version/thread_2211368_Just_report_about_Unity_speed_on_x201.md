---
title: "Just report about Unity speed on x201"
date: 2014-03-15
forum: Ubuntu Development Version
---

### Post by forcecore on 2014-03-15
I want to tell that compared to 13.10 Unity is lot more snappy on my x201, i do not know what devs optimized but thanks.

---

### Post by Sophont on 2014-03-15
I can confirm that.

14.04 feels noticably snappier on my Aus F201E (2 GB version that came pre-installed with Ubuntu 12.04).

Apart from a Bluetooth regression everything has been great after upgrading to 14.04 last week.

---

### Post by forcecore on 2014-03-29
i update raport about both my i5 2400 desktop pc and i5 laptop with Ironlake GPU(intel HD) is rock solid with 14.04, way snappier than 13.10 was(i use Unity), 64 bit.

I want to ask is there someone who has older IBM laptop with Core duo or Core2 duo age? do you had any problems? Someone wanted 14.04 on X60 and it had some temporary graphics freeze problems but was usable. Kernel 3.14 solved this so there is nothing big just i like to know.

---

### Post by monkeybrain20122 on 2014-03-29
> **forcecore said:**
> i update raport about both my i5 2400 desktop pc and i5 laptop with Ironlake GPU(intel HD) is rock solid with 14.04, way snappier than 13.10 was(i use Unity), 64 bit.

I want to ask is there someone who has older IBM laptop with Core duo or Core2 duo age? do you had any problems? Someone wanted 14.04 on X60 and it had some temporary graphics freeze problems but was usable. Kernel 3.14 solved this so there is nothing big just i like to know.

Do you use the package libvdpau-va-gl? I use it to get vdpau decoding for videos with the ironlake gpu (mostly for mplayer and flash which don't use vaapi) In 13.10 I install it with the webupd8 ppa (along with mesa drivers from the oibaf ppa) and it works quite nicely. In 14.04 it is in the repo but it didn't work when I tried two weeks ago (vdpauinfo exited with error) I plan to get a new image and try again in a few days. But since you use the same intel driver I would like to hear your experience.

---

### Post by forcecore on 2014-03-29
> **monkeybrain20122 said:**
> Do you use the package libvdpau-va-gl? I use it to get vdpau decoding for videos with the ironlake gpu (mostly for mplayer and flash which don't use vaapi) In 13.10 I install it with the webupd8 ppa (along with mesa drivers from the oibaf ppa) and it works quite nicely. In 14.04 it is in the repo but it didn't work when I tried two weeks ago (vdpauinfo exited with error) I plan to get a new image and try again in a few days. But since you use the same intel driver I would like to hear your experience.

For all multimedia i use VLC only, no other players. Videos play very well on my pc-s.

---

