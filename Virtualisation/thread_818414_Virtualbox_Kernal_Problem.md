---
title: "Virtualbox Kernal Problem"
date: 2008-06-04
forum: Virtualisation
---

### Post by arak on 2008-06-04
It seems that every time I upgrade the "Kernal"--I think that is what is called (I'm a Newbie)--my Virtualbox stops working.  I found a simple way to correct the problem.  Just reinstall Virtualbox and it starts working again without any loss of data.

---

### Post by tighem on 2008-06-04
That is because virtualbox uses kernel modules it creates locally against your installed kernel headers. Change the kernel and you have to rebuild the modules. There's a script to do it without reinstalling but it usually fails for me on VB 1.6. Reinstalling definitely works.

---

