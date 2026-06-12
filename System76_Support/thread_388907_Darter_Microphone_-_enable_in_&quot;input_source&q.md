---
title: "Darter Microphone - enable in &quot;input source&quot;"
date: 2007-03-20
forum: System76 Support
---

### Post by cowbean on 2007-03-20
The microphone on my Darter Ultra didn't seem to be working out of the box.  First I tried updating the System76 drivers (with the .deb in the /darter directory of the system76 repositories -- not sure if this was a necessary or good idea), but to no avail.

Eventually figured out how to get it working.  The microphone is actually working, but the source is "Front Mic" and not "mic", which is the default input source.  I tested by unmuting and maxing "Front Mic" on the playback levels tab -- resulted in near-deadly feedback.

To fix, open up the Volume Control Panel, and in the menus go Edit -> Preferences.  Scroll down and check the "Input Sources" box.  This should add a fourth tab to the Volume Control Panel, called "Options".  There, you can change the input source to "Front Mic".

Hope this helps.  System76, you guys may want to make this the default setting for Darter Ultras.

---

