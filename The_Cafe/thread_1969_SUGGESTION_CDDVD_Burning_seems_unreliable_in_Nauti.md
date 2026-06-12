---
title: "SUGGESTION: CD/DVD Burning seems unreliable in Nautilus/GNOME"
date: 2004-10-24
forum: The Cafe
---

### Post by jdong on 2004-10-24
Symptoms: When burning with Nautilus-cd-burner, you seem to make more coasters/failed burns than with your favorite burning program from another distro.


Possible answer: Burn-proof protection is OFF by default.


FIX:

1. Press ALT+F2, run gconf-editor. Or, find it from the menu.
2. Navigate the gconf editor to /apps/nautilus-cd-burner/.
3. Check Burnproof.


While in there, you may be interested in changing the tmp folder (where mkisofs puts the iso) and/or overburn settings.

---

### Post by mark on 2004-10-25
Interesting - I've burned multiple CDs and a couple of DVDs (I'm a distro/upgrade junkie) with *Nautilus* and haven't had any problems.  I haven't touched any of the default settings, either.
  
 I've noticed from a number of posts that I've been very lucky with having things "just work" right from the start. I wonder if it's due to the "vanilla", standard nature of my hardware? I'm running an Intel D865GLC mainboard, using all of the on-board features (audio, Ethernet, video, etc.). My optical drive is a LITE-ON SOHW 812S DVD+RW.

---

### Post by jdong on 2004-10-25
Unless you are running too many disk and CPU intensive programs at the same time, there's NO REASON why a modern PC (300MHZ+) running Linux 2.6.x wouldn't be able to satisfy a ~3MB/S data stream. That's why you haven't seen any issues.

Of course, it sucks when switching to a VT or accidentally starting OO.o on a old comp ruins a disc... ;)

---

