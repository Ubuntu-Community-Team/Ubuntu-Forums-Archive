---
title: "memory usage on bootup"
date: 2010-03-26
forum: System76 Support
---

### Post by ethanay on 2010-03-26
FYI

For quite a while, the Meerkat Nettop was consistently using an amazing 15-30% of its 2gb memory (not upgradable) on startup.

This was concerning for me:  I suggested my dad (new to Linux) buy this system, knowing that my 2gb laptop only uses ~5% of its memory on startup.  I figured there was still plenty of room to "grow," especially since the most demanding programs he uses are Firefox, Stellarium and 2d CAD.

I fixed a corrupted hosts file, restarted the computer, entered the BIOS setup for the first time, enabled the HPET feature, rebooted, and memory usage went down to the expected 5%.

I disabled the HPET feature again, but memory usage stayed low.  Very strange!  I'm leaving HPET enabled.

I have no idea if enabling HPET or even entering the BIOS setup for the first time had anything to do with it.  But I'm glad memory usage is more reasonable.  The system also feels more responsive, now.

---

### Post by thomasaaron on 2010-03-29
I just just put our stock image on a Meerkat, and I was able to go to CUPS admin. Not sure what fouled it up, but it doesn't seem to be the factory image.

---

