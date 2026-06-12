---
title: "rdesktop on two workplaces (WinXP under VirtualBox)"
date: 2009-10-16
forum: Virtualisation
---

### Post by corsakh on 2009-10-16
Hey guys,

I am totally new to linux. Trying to virtualize Windows XP on my workplaces. I run it under VirtualBox and it works fine. I followed a guide here on this forum using rdesktop to seamlessly integrate Windows XP into Ubuntu environment. Works good, I am happy with the result. But the Windows part is limited to one workplace. I'd like to span it over two workplaces. Is there any way to do it using VirtualBox, rdesktop or anything else?

UPDATE: I have manged to span it over two workplaces using a command

VBoxManage controlvm "Win" setvideomodehint 3260 1002 32 0

But now Windows is very slow. VM has 1gb RAM and 128mb video. Can I do anything to improve the situation?

Thank you.

---

