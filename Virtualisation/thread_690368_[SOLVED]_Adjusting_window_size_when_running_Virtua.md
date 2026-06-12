---
title: "[SOLVED] Adjusting window size when running Virtual Box"
date: 2008-02-07
forum: Virtualisation
---

### Post by geo909 on 2008-02-07
Hello everybody.

I have installed both OpenSUSE 10.3 and windows XP under Virtual Box. Everything is fine except one thing:

 The window size of VB is too tiny, and I really can't work like that. There is an option for "full screen" but when I choose that, the window size stays the same and the rest of the screen turns black, that's all.

 Do you have any idea how I could fix that?

---

### Post by p_quarles on 2008-02-07
Moved to Virtualization.

To enable a full-screen display, you'll need to install the guest additions for each OS. The first step is to get the installation files, which can be done by clicking on "Device" while the machine is booting.

The procedure for installing is slightly different for each OS, but relatively straightforward.

---

### Post by jabeez on 2008-02-07
I've only used XP through VirtualBox, but in addition to installing guest additions to get full screen, if you change the resolution within the virtualized OS it should change the window size to whatever resolution you pick, so pick a resolution slightly lower than your regular desktop and you should have a workable windowed OS.

---

### Post by geo909 on 2008-02-07
**@p_quarles**

Yep, that did the job (at least in windows XP, haven't tried on SUSE)!

Thanks a lot!!

P.S. @jabeez Yes, I had noticed that. However with the solution above I also have full screen.. Very convenient!!

---

