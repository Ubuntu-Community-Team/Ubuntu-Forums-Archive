---
title: "[SOLVED] U14.04 + Virtualbox 4.3.10: Windows 7 and Windows XP won't install"
date: 2014-04-29
forum: Virtualisation
---

### Post by yan4 on 2014-04-29
Here we go for one more chapter in my personal nightmare with Virtualbox.

My current OS is Ubuntu 14.04 with Virtualbox 4.3.10.

VB starts and flowlessly creates the virtual machines (Windows 7 64 and WIndows XP 32).

After I boot the machines with their respective CDs everything goes fine until the install process starts and tells me that there is something missing.

[COLOR=#ff0000]**My boot CDs are fine and works perfectly everywhere but in the Virtualbox.**[/COLOR]

This is what W7 shows me:

[IMG]http://i.imgur.com/4iAjzCL.jpg[/IMG]

This is what WXP shows me:

[IMG]http://i.imgur.com/Nfot3ow.jpg[/IMG]

I never got those screens before in my whole life.

Any idea?

---

### Post by yan4 on 2014-04-29
After some research, phone calls and attempts the solution came up.

Actually it is pretty simple after you know that.

To solve the 'missing driver' issue along the system install, just go to the main screen of Virtualbox, click 'settings' (the yellow gear) of the problematic machine, then 'storage' in the list. Then click onto the CD icon and ensure that the option 'Passthrough' is CHECKED. The problem will disappear.

:)

---

