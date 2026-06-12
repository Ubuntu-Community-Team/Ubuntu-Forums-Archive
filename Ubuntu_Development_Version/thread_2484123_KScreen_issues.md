---
title: "KScreen issues"
date: 2023-02-18
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2023-02-18
Anyone running Lunar with plasma desktop (x11 + nvidia 525.85.05 drivers) notice issues with KScreen in the past week or two?  I only noticed because my secondary monitor is to the left of my main monitor and they were flipped after a reboot in the last week.

When I go to Display Configuration, it claims "No KScreen backend found.  Please check your KScreen installation."  
[ATTACH=CONFIG]291816[/ATTACH]

- Re-installing kscreen seems to do nothing to fix the problem.
- kscreen_backend_launcher is running when I look at processes.

kscreen-doctor --info currently says
```
Environment: 
  * KSCREEN_BACKEND           : [not set]
  * KSCREEN_BACKEND_INPROCESS : [not set]
  * KSCREEN_LOGGING           : [not set]
Logging to                : [logging disabled]
Preferred KScreen backend : KSC_XRandR.so
Available KScreen backends:
  * KSC_Fake.so: /usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kscreen/KSC_Fake.so
  * KSC_KWayland.so: /usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kscreen/KSC_KWayland.so
  * KSC_QScreen.so: /usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kscreen/KSC_QScreen.so
  * KSC_XRandR.so: /usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kscreen/KSC_XRandR.so
  * KSC_XRandR11.so: /usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kscreen/KSC_XRandR11.so

```
though I've tried setting the env variables directly to no success.

---

### Post by xyz-t on 2023-02-20
The screenshot shows an old version of the plasma, highlight changed settings is not bottom left since 4-5 weeks (top left, hidden).  Plasma 5.27.0 is ok and kscreen-doctor --info is fine using wayland.

Give it a try.

Kubuntu backports ppa:
[https://community.kde.org/Kubuntu/PPAs](https://community.kde.org/Kubuntu/PPAs)
```

$ sudo add-apt-repository ppa:kubuntu-ppa/backports
$ sudo apt update && sudo apt full-upgrade -y
```

---

### Post by 3vi1 on 2023-02-21
Thanks for the info.  Looks like they simply haven't finished pushing the newer plasma 5.27 packages to the devel repos.  I'll wait for them to hit there; I don't want to complicate testing by adding the kubuntu backports ppa.

Thanks!

[Edit:  2023-02-28 - Updates to main repos fixed everything.  I did a re-install to pull in plasma-desktop again to grab any changed dependencies, just in case because I saw others reporting problems on Reddit this morning]

---

