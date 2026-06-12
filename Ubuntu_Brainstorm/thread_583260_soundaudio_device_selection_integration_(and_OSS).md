---
title: "sound/audio device selection integration (and OSS)"
date: 2007-10-20
forum: Ubuntu Brainstorm
---

### Post by slavik on 2007-10-20
If a user has more than one sound card, there are multiple screens/ways to select a sound card for different things. One is for ALSA, another is for gstreamer

There should be an app with tabs for ALSA and OSS. Selecting a tab shows a short description at the top of the tab.

Then there is a drop down list for cards.

ALSA: Allows selection of any card
OSS: Allows selection of any card plus an entry for ALSA (if ALSA is selected, all OSS apps are forced to go through dmix/dsnoop).

Gstreamer should use ALSA by default. Also, could there be some new environment variables for default audio/video input/output?

---

### Post by Zdravko on 2007-10-20
+1.

---

