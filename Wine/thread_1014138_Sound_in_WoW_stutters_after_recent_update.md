---
title: "Sound in WoW stutters after recent update"
date: 2008-12-17
forum: Wine
---

### Post by b4t3m4n on 2008-12-17
I installed 8.10 64, and installed wine off of winehq (1.1.10) and ran WoW.  It ran without issue, and was pretty speedy.  I have never had a problem with Wine/Linux/WoW on my machine before, and didn't expect one either.

Yesterday I think, I installed 32 updates or so and now WoW's audio stutters.  I added the two related audio config lines from the wiki into my config.wtf but it didn't help.  

I have no idea what update could have affected it.  I also installed and tried it in an openbox session (no gnome-settings-daemon), same result.

---

### Post by shatteredmindofbob on 2008-12-17
I'm thinking regression. Sound stutters in EVERYTHING I try under 1.1.9/1.1.10

Searching for workarounds but not finding any...

---

### Post by psychok9 on 2008-12-28
Same problem here.
With last build 1.1.10 on WineHQ repository the sound stutters!
With last build (today) on Ubuntu repository, works great... but Wow + Wine sometime crash.

Q6600@3.2GHz
Ubuntu 8.10 x86_64
X-Meridian 7.1

---

### Post by psychok9 on 2008-12-28
Fixed with *"Driver emulation"* flag on the box of Winecfg!

---

