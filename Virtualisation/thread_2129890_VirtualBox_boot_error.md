---
title: "VirtualBox boot error"
date: 2013-03-27
forum: Virtualisation
---

### Post by Xenoverse on 2013-03-27
I'm attempting to run Windows 7 (64 bit) as guest from Ubuntu 12.10 with VirtualBox (installed through Software Center). When I tried to start Windows for the first time (with install disk in drive and boot order set to CD/DVD first), I get ```
FATAL: No bootable medium found! System halted.
``` What do I need to do to get it working?

---

### Post by ibjsb4 on 2013-03-27
You do not set the boot order, thats for host only.  You select it from the guest screen when installing.

[ATTACH=CONFIG]240614[/ATTACH]

---

### Post by Xenoverse on 2013-03-27
I got it now. For some reason when it gave the first boot prompt and I select the drive it doesn't work, I had to go to Settings > Storage and change the IDE controller to the proper drive. Working now though :)

---

