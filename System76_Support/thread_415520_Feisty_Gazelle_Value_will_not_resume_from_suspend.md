---
title: "Feisty: Gazelle Value will not resume from suspend"
date: 2007-04-20
forum: System76 Support
---

### Post by AusIV4 on 2007-04-20
I just upgraded my Gazelle to Feisty. Initially I tried a dist-upgrade, but that had a number of problems (for one thing, my swap partition wasn't activated). I decided to install from CD, and everything seems to work, except it won't resume from suspend. Hibernate works fine, but with suspend the lights turn on and the hard drive clicks, but the screen never even turns on.

I ran the System76 driver, and it informed me that this system's hardware was fully supported by the default Ubuntu install.

It's no big deal, I've been using hibernate pretty much exclusively since hotkeys don't work after suspend, but it does seem like this is something that ought to be fixed.

[EDIT] I also have no sound. I have filed bug reports for each of these problems.

---

### Post by crichell on 2007-04-20
Thanks for the bug reports - we'll send down a driver fix within a couple of hours.

For the suspend issue please post your acpi-support file.  It's easier to track and solve bugs over in launchpad so you may want to post it there:

[https://bugs.launchpad.net/system76/+bug/108253](https://bugs.launchpad.net/system76/+bug/108253)

---

