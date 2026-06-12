---
title: "screen resolution issue : virtualbox : WinXP"
date: 2010-03-10
forum: Virtualisation
---

### Post by Beowulf.1000 on 2010-03-10
Any ideas on how I might achieve 1280x800 as a resolution mode in Windows XP running virtualized under Virtualbox? I have Ubuntu 9.10 x86 64bit installed fine, with 1280x800 resolution, and with Virtualbox with an installed Windows XP Professional. But I can not get the 1280x800 resolution in the virtualized winxp, it does not show up as a choice, such that when i run full screen virtualbox winxp my WinXp is not making full use of the width of the screen. Best I can get is 1024x768 and the higher resolutions that are available behond that exceed the 800 max height so that my taskbar and start menu would disappear. What I want to achieve is 1280x800 then my virtualized winxp will look sweet and make perfect use of the screen.

Ubuntu 9.10 (and Windows Vista on other partition) are displaying 1280x800 as full resolution and screen height and width; intel 965 express chipset.

---

### Post by kgarbutt on 2010-03-10
I had the same problem with my windows in vituralbox. You have to install guest additions for it to work. Also search the ubuntu forum there are posting regarding it as well.

---

### Post by Beowulf.1000 on 2010-03-10
EDIT: Nice! Thank you so much! After installing the guest addition, now when I do the host+f to go fullscreen, WinXP is showing 1600x900 (my highest res) and fills the entire monitor. This is so important to me, because I was wanting as much screen real estate as possible to run my screenwriting software, and also music composition software; Movie Magic Screenwriter, Sibelius 6, both which installed and run nice in virtualbox.

okay i just figured out how to install a guest addition, but I can't see how that let's me boost my virtualized WinXP screen resolution. E.g. on my desktop now (where I added the guest addition) I can only get 1024x728, but my Ubuntu is doing 1600x900 (nvidia graphics).

---

