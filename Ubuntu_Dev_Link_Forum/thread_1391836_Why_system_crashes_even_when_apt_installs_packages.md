---
title: "Why system crashes even when apt installs packages after checking dependencies??"
date: 2010-01-27
forum: Ubuntu Dev Link Forum
---

### Post by kapmsd on 2010-01-27
Hi guys!!
APT is more popular because of its dependency checking even with installation of 3rd party softwares.
I wonder why then system crashes after updates (listed down in the update manager).
This is a common problem in 9.04,9.10 .
Myself and my friends have experienced it.
Is there any fault with apt then?

---

### Post by arubislander on 2010-01-27
Could you show us the reported crash message?

---

### Post by kapmsd on 2010-01-27
I will attach a picture caused by video driver problem.
Just after updating ubuntu 9.04 , i rebooted to get this.
After that i had to reinstall ubuntu.

---

### Post by arubislander on 2010-01-28
That doesn't seem like a system crash... looks more like a video card driver issue...

With the display as it is, do you eventually hear the login prompt sound? (do they still have that in Karmic?)

---

### Post by kapmsd on 2010-01-28
Ya,My case isn't a system crash.
But my friend using karmic got his system crashed after updating all updates  listed in update mgr.
Take my case,
APT would have resolved all dependencies b4 installing any update.
So why such problems like video card driver,system crash happens?

---

### Post by arubislander on 2010-01-28
apt only checks package dependencies, it has no way of knowing that the software in the installed packages will actually work with your hardware. 

So if all the dependencies have been met the packages get installed. If the software then has issues with your hardware, then crashes / driver problems / black screens of death may occur.

---

### Post by Safwan Khan on 2010-01-28
I think you need to boot in the recovery mode and disable your video driver followed by a normal mode boot. Once there, better remove your current video driver. there are many tutorials available about it on the internet. And next time you update your system, make sure that you are not installing incompatible video drivers on your machine to avoid any future issues.

---

