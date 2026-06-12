---
title: "Fix sound problem in Musescore in Ubuntu Mate"
date: 2014-11-17
forum: Tutorials
---

### Post by stevecook on 2014-11-17
I just installed Musescore in Ubuntu Mate and found that it would not play any sound. Nor would any other sound application play any sound while Musescore was running. After a bit of digging around, I found the following solution fixes the problem:

Open a terminal.

Type:

**sudo apt-get install gawk**

When installed, close the terminal.

Log out and then back in to Ubuntu Mate.

That's it. You should find if you re-open Musescore, the sound will work and there will be no other associated system-wide sound problems while it is running.

---

