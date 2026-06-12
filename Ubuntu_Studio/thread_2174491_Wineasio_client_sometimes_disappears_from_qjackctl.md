---
title: "Wineasio client sometimes disappears from qjackctl/patchage"
date: 2013-09-14
forum: Ubuntu Studio
---

### Post by halfbeing on 2013-09-14
I have added wine-rt and wineasio to my Ubuntu Studio 13.04 and I use them to run Reaper. Reaper connects to the Jack server OK and I get sound from the speakers. The trouble is that it often vanishes from the QJackCtl graph for no apparent reason, sometimes within a couple of seconds after launch, meaning that I cannot connect it to other Jack clients, even though it continues to function and to send sound to the speakers. When it is invisible to QJackCtl it is also invisible to Patchage. Is there anything I can do about this?

---

### Post by halfbeing on 2013-09-15
The problem turned out to be a setting in Reaper, "Close audio device when stopped and application is inactive", which can be disabled in the preferences.

---

