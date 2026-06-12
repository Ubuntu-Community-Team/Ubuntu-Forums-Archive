---
title: "video mode not supported"
date: 2010-02-10
forum: Wine
---

### Post by djpupeikis on 2010-02-10
hello.

when I run Stronghold Crusader by Wine, my monitor gets black, and displays only mode not supported.
How to solve this issue? 
I am using GF gt7300, monitor xerox xa7-17i. Nvidia drivers installed.

In another hand, when launching CS:S I add specific parameters such as resolution 1024x768 and -refresh 59.91 It helps for "mode not supported" issue.

Unfortunately I can't add specific parameters to Stronghold crusader game.
I need to somehow make system understand supportable frequency and resolution...

Thanks!


edit.
I had same problem installing ubuntu. So I just changed video cards temporally until I downloaded nvidia graphic drivers.

---

### Post by djpupeikis on 2010-02-14
any help?...

---

### Post by Soulcage on 2010-02-14
Some games just won't work in fullscreen like bf1942 so you need to turn on "emulate a virtual desktop" in winecfg's graphics tab, you can set it just below your desktop resolution since it shrinks and grows to size. Then close all windows programs "wineserver -k" if need be then run it.

---

### Post by djpupeikis on 2010-02-14
Worked, thanks!

---

