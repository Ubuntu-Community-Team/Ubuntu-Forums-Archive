---
title: "What are the plans for adopting GTK 3?"
date: 2011-04-28
forum: The Cafe
---

### Post by murderslastcrow on 2011-04-28
So, Unity rocks, it's great- good execution. Very stable and usable. Yadda yadda. So, now that we get the argument for Unity being a good choice out of the way, I'm wondering how exactly we're going to move to GTK 3.

For example, Nautilus, Gedit, File-Roller, and Banshee are all moving onto GTK 3 without turning back (except for maybe a GTK 2 version of Banshee). So, assuming that we will have GTK 3 versions of the default themes in Ubuntu by the next release, how do we plan on configuring themes? Are we just going to make a new theme selection interface for selecting matching GTK 2 and 3 themes? Are we going to do something similar to QtCurve or QGTKStyle to make a GTK 3 that looks like a current GTK 2 theme, or vice versa?

We only have six months to figure this out before we start abandoning new programs and looking old. Anyone have a clue as to where we could find information regarding this issue?

---

### Post by godhika on 2011-04-28
Well Andrea Cimitan already ported the Murrine engine to Gtk+3 last fall, and since then there has been a gtk+3 version of the light-themes (if you look under /usr/share/Themes/Ambiance/ you see for example the gtk+2 and gtk+3 files). Further steps are discussed at the moment and this will be a topic at UDS.

---

