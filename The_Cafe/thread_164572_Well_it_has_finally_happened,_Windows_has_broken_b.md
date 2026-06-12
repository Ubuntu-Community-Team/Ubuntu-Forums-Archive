---
title: "Well it has finally happened, Windows has broken but Ubuntu works"
date: 2006-04-23
forum: The Cafe
---

### Post by blastus on 2006-04-23
About a month ago I bought a LCD monitor and hooked it up my computer with a DVI cable. Unfortunately I can't get it to work with Windows XP. If I run Windows in my LCD's native resolution, 1280x1024, the screen becomes unstable. Every time I move the mouse or do something like open or close a menu or a window, the screen goes black for a few seconds then appears again. I had the same issue on Ubuntu, but I fixed it by setting the horizontal and vertical sync/refresh rates in /etc/X11/xorg.conf to my monitor specs:

HorizSync	30-81
VertRefresh	56-75

I've tried re-installing the NVIDIA driver on Windows. I've spent hours playing around with the NVIDIA control panel and display settings. I've searching the registry, the Microsoft website, and the Internet. There's just no place anywhere where I can enter in the horizontal sync range for my monitor.

To be fair, I did have wierd DVD/video playback issues on Ubuntu, like tearing artifacts and horizontal lines, but I managed to solve that problem by adding the following lines to the "Device" section in /etc/X11/xorg.conf

Option          "TwinView"
Option          "MetaModes" "DFP-0: 1280x1024, CRT-0: 1280x1024"
Option          "TwinViewOrientation" "Clone"
Option          "ConnectedMonitor" "CRT-0, DFP-0"

I still don't think Ubuntu is easier to install than Windows, but crap like this makes want to punch the next person who says "Windows works out of the box." ](*,)

---

### Post by dermotti on 2006-04-23
Ide reinstall windows!

---

