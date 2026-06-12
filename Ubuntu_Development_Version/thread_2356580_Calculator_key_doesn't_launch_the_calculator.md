---
title: "Calculator key doesn't launch the calculator"
date: 2017-03-24
forum: Ubuntu Development Version
---

### Post by Yahoé on 2017-03-24
In 17.04 using Unity, the calculator key doesn't launch the calculator. This started a couple months back but still is happening (on two different machines) as 17.04 is nearly released. Is anyone else experiencing this problem? If I had to open a bug report, against which package?

---

### Post by fthx on 2017-03-24
Not Unity because it affects since some time my Zesty Gnome...

---

### Post by jbicha on 2017-03-24
Thanks for mentioning the issue. That's GNOME [bug 780348]("https://bugzilla.gnome.org/show_bug.cgi?id=780348") and will be fixed in Ubuntu 17.04 Beta soon with gnome-settings-daemon-schemas 3.24.0-0ubuntu2.

---

### Post by fthx on 2017-03-26
ok it works now !

---

### Post by thie on 2017-04-17
I upgraded from 16.10 to 17.04 a few days ago and now suffer from this issue, the calculator won't start via the calc key or any other shortcut key that I assign.
All of this despite the fact that the fix for this bug was seemingly included as it's running:

gnome-settings-daemon (3.24.0-0ubuntu2) zesty; urgency=medium

  * Add git_fix-calculator-key.patch:
    - Fix Calculator keyboard key with gnome-calculator 3.24

 -- Jeremy Bicha <jbicha@ubuntu.com>  Fri, 24 Mar 2017 19:55:10 -0400

---

### Post by jbicha on 2017-04-18
Oops, I needed to [fix this]("https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1676431") on Unity too so we'll have to do a Stable Release Update for this now.

---

