---
title: "What The Heck Are Nautilus Metafiles?"
date: 2009-03-17
forum: Security
---

### Post by SuperMike on 2009-03-17
Anyone know what the heck are Nautilus metafiles? You can find them by doing this:

$ ls ~/.nautilus/metafiles/

And you might be surprised to find out what's in one of them. It appears to keep some kind of history about icons or file locations? Is it some kind of cache? And why are these things not encrypted?

---

### Post by LegendofTom on 2009-03-17
Probably XML files.  I think at least one keeps record of every file put on the desktop.  You could always open them up and check them out.

---

### Post by Vadi on 2009-03-17
Looks like it stores stuff like per-directory preferences (like what type of view do you want, scale of icons) in it.

---

### Post by zika on 2009-03-19
we had discussion about that in [http://ubuntuforums.org/showthread.php?t=1068084](http://ubuntuforums.org/showthread.php?t=1068084). You might find it useful. I started it and I have learned a lot.

---

