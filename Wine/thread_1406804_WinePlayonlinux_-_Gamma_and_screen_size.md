---
title: "Wine/Playonlinux - Gamma and screen size"
date: 2010-02-14
forum: Wine
---

### Post by Boulemans on 2010-02-14
I managed to get the 3D acceleration working on my laptop. Installed Jedi Knight II, Jedi Outcast - all works fine
BUT: can't change many video settings. Screen gamma and screen size are just two examples of that. (Wine: 1.1.37, ubuntu 9.04, ati xpress 1150). Screen size is fixed on what appears to be 640x480

Somethimes the system logs me out when trying to change those settings.
can anyone help with this?

---

### Post by asdfoo on 2010-03-12
> **Boulemans said:**
> I managed to get the 3D acceleration working on my laptop. Installed Jedi Knight II, Jedi Outcast - all works fine
BUT: can't change many video settings. Screen gamma and screen size are just two examples of that. (Wine: 1.1.37, ubuntu 9.04, ati xpress 1150). Screen size is fixed on what appears to be 640x480

Somethimes the system logs me out when trying to change those settings.
can anyone help with this?

you need to look at the modes setup for your x server, eg check `xrandr`.

what happens when you try to adjust gamma?

---

