---
title: "will upgrade to final from dailly beta possible?"
date: 2016-04-17
forum: Ubuntu Development Version
---

### Post by erkanea on 2016-04-17
Hello.
I would like to install Xubuntu 17th of April daily version, but I wonder if it will be possible to upgrade to final LTS version from beta?
Regards.

---

### Post by Bucky Ball on 2016-04-17
After install,

```
sudo apt update
sudo apt full-upgrade
```

... each day until the 21st (and beyond) should get you there. I did see a discussion somewhere about the pros and cons of the daily and the beta 2, but not sure. Maybe someone can clarify.

---

### Post by ajgreeny on 2016-04-17
Even if you started some time ago with 16.04, as I did, and regularly updated, you would still end up with the same released version, the same as if you had installed after final release.

However, it is possible that there might be some unnecessary cruft in the system following so many package upgrades and new packages being installed as development went on, and there were very many.  Some packages were removed as this procedure occurred, but maybe not all were, so it would probably be worthwhile running ```
sudo apt-get autoremove
``` to make sure all packages that are no longer needed are removed from the system.

---

### Post by grahammechanical on 2016-04-17
There is no such thing as a daily beta. What there is throughout the 26 week development period are daily built ISO images. Some of which are designated Alpha 1 & 2 and Beta 1 & 2. Although these designations are used by the Ubuntu flavours as milestones they are not used for Ubuntu any more.

Install the final Beta and we will get the code as it was on 24th March. Update/upgrade and we get the code as it is today 17th April. The same code that is in the daily ISO image built for the 17th April.

Anyone who installed the first xenial xerus daily image about 24 weeks ago and updated/upgraded regularly will have an installation as up to date as that installed from the final release ISO image.

[https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule](https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule)

Regards.

---

### Post by erkanea on 2016-04-18
thank you very much everyone. I will start with 17th of april build now as older versions causing some problem with dual gpu, wifi adapter and touchpad.

---

### Post by Bucky Ball on 2016-04-18
Good luck. Be sure to post new threads about any issues you have with the latest build. This will give you the best chance of support as the question asked here and in the title of the thread has been answered/solved (please see the first link in my signature below to mark it so). :)

---

