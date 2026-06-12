---
title: "Compiz cube"
date: 2008-05-27
forum: System76 Support
---

### Post by riseringseeker on 2008-05-27
I've posted requests for help elsewhere on the board, but thought I would drop one in here as well, as this is the only problem than I've had since updating the daru1 to 8.04 (the other problem is in a different thread)

When I try to activate the rotating cube it works fine UNLESS I have any applications on the desktop.  If any app or window is visible on the desktop, the system crashes, and goes to the log in, it works if they are minimized though.

I haven't done this often enough to catch the error messages yet, but will do my best to copy them down.

---

### Post by thomasaaron on 2008-05-27
The cube works perfectly on my DarU1. If you upgraded, perhaps there is a hosed configuration in .compiz that is messing it up. Try changing the name of .compiz and then doing: sudo apt-get --reinstall install compiz compiz-core

---

### Post by riseringseeker on 2008-05-27
> **thomasaaron said:**
> The cube works perfectly on my DarU1. If you upgraded, perhaps there is a hosed configuration in .compiz that is messing it up. Try changing the name of .compiz and then doing: sudo apt-get --reinstall install compiz compiz-core

Nope, clean install 64bit 8.04 with all updates.

Have uninstalled reinstalled, same thing.

Cube works great for me too, as long as I don't have any apps showing.  If I have no apps open, or minimized to tray works fine, any open, it crashes.

---

### Post by riseringseeker on 2008-05-28
I was told to try to disable 3D effects, and that now works.  So I will mark this one (mostly) solved.

---

