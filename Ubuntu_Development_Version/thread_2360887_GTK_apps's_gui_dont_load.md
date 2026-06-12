---
title: "GTK apps's gui dont load"
date: 2017-05-09
forum: Ubuntu Development Version
---

### Post by dino99 on 2017-05-09
Get that issue with Zesty (and i can only open a unity session, others end with a black screen); and also with an Artful fresh netinstall.
Synaptic, for example, in a terminal, does not show error/warning; the gui fails to load.

---

### Post by Smask on 2017-05-10
I wonder if this is connected to the same issue that I've got. "gnome-panel crashed with SIGSEGV in gtk_bin_forall()" lp bug 1689680 (marked as private at the moment but the heat immediately went to 158 when entering data). I can't log in using Gnome Flashback. The session come as far as loading the wallpaper and then I get thrown back to the login screen again.

---

### Post by dino99 on 2017-05-11
i dont get crash in my case.

---

### Post by corradoventu on 2017-05-11
I have the problem in Artful only in gnome wayland session: [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1551951](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1551951)
in Artful Unity and Gnome classic synaptic works fine.

---

### Post by dino99 on 2017-05-11
The problem is solved on a new Artful install, but without a crypted home that time as proposed by ubiquity. And the 24" display was detected as an 42" ;) , so all the menu and icons were out of view.
But i still have that issue with Zesty.

---

### Post by #&amp;thj^% on 2017-05-11
> **dino99 said:**
> Get that issue with Zesty (and i can only open a unity session, others end with a black screen); and also with an Artful fresh netinstall.
Synaptic, for example, in a terminal, does not show error/warning; the gui fails to load.
If this is gnome-shell session see this: [https://ubuntuforums.org/showthread.php?t=2358026](https://ubuntuforums.org/showthread.php?t=2358026)
I added a little something to my .bashrc and no problems.

---

