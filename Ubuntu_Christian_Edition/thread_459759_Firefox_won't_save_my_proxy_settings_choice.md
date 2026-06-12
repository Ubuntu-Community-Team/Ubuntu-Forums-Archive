---
title: "Firefox won't save my proxy settings choice?"
date: 2007-05-31
forum: Ubuntu Christian Edition
---

### Post by naked on 2007-05-31
I just noticed today that my filter seems to not be working.

When I go into Preferences -> Advances-> Network -> Settings.  It was setup to Direct Connect.  The proxy info was still in there, just not selected.  I can select it, and the filter works.  But if I close all sessions and re-open, it goes back to Direct Connect.

I've messed with the DansG Gui to lock and unlock the proxy settings, but this doesn't seem to do anything.  Any advice?

L

---

### Post by spin2cool on 2007-05-31
Seen this?
[http://forums.mozillazine.org/viewtopic.php?p=2901384&sid=3af6a263c4960fa9b1320e21f55e7076](http://forums.mozillazine.org/viewtopic.php?p=2901384&sid=3af6a263c4960fa9b1320e21f55e7076)

also might check the permissions of your prefs.js - make sure the setting is getting saved correctly.

---

### Post by mhancoc7 on 2007-05-31
> **naked said:**
> I just noticed today that my filter seems to not be working.

When I go into Preferences -> Advances-> Network -> Settings.  It was setup to Direct Connect.  The proxy info was still in there, just not selected.  I can select it, and the filter works.  But if I close all sessions and re-open, it goes back to Direct Connect.

I've messed with the DansG Gui to lock and unlock the proxy settings, but this doesn't seem to do anything.  Any advice?

L

Sounds like the bug that was fixed with the latest release of Ubuntu CE.

You can go [here]("http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html") and download and run the latest script to up date your dansguardian  setup. Then you should be able to unlock and change your proxt settings, and they should stick.

Jereme

---

