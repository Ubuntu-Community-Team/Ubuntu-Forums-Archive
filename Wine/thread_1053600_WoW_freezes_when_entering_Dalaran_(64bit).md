---
title: "WoW freezes when entering Dalaran (64bit)"
date: 2009-01-28
forum: Wine
---

### Post by Bad_Byte on 2009-01-28
Few days ago I did a clean upgrade from Kubuntu 7.10 64bit to Kubuntu 8.04.1 64bit.

Ever since the upgrade WoW freezes when entering or getting near Dalaran. Installed latest wine and nvidia drivers, even tried using same wine version and nvidia driver versions as used on the previous kubuntu install, no luck.

Any ideas for a fix?

---

### Post by Ferrat on 2009-01-28
If you don't have any addons on (if you do turn them off and try) the it could be a corrupt file, try using blizzards repair program and if that doesn't work reinstall, there are a number of issues with WoW on any system since the WotLK release for the mystical graphic errors and file corruptions that happens for a lot of ppl, for ex. I know my WoW is corrupt but in Win XP I can play it, however wine catches the problem, I fix it it works for a time and then graphic crash and it's back again and it's not even the Graphic part that becomes corrupt, it's the data handler for achivements ^^ 

I've heard lot of weird problems and all started after release more or less, hmm could it be the new devs can't hack it:oops:

---

### Post by Bad_Byte on 2009-01-29
After some searching it turns out to be a bug made by lazy wine developers that affects systems with 4 or more GB of ram.

**Solution: Reduce physical ram to less than 4GB**

---

### Post by Bad_Byte on 2009-01-29
delete this post

---

### Post by ender1598 on 2009-02-10
Do you have a source for this solution?  I've got 6 gigs of ram on a 64 bit system and have noticed regular crashes.  Still trying to find the cause but this might be part of it.

---

### Post by Bad_Byte on 2009-02-11
Source that would be me, I have not experienced a single crash since I lowered my physical RAM to 3GB, not an ideal fix but it works for me =|

---

