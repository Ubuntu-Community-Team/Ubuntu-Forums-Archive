---
title: "Bottom panel is still visible when I enable virtual desktop"
date: 2009-04-29
forum: Wine
---

### Post by hotweiss on 2009-04-29
Bottom panel is still visible when I enable virtual desktop. This has never happened to me before. I am using wine 1.20 and Ubuntu 9.04. Here is a screenshot:

[IMG]http://img90.imageshack.us/img90/4876/screenshot1b.png[/IMG]

---

### Post by hotweiss on 2009-04-29
OK I have found the solution. Install compiz settings manager:

> sudo apt-get install compizconfig-settings-manager

Go into Compiz Settings, then Workarounds and enable Legacy Fullscreen Support.

---

