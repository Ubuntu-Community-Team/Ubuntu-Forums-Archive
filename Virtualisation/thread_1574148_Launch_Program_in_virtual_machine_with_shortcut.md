---
title: "Launch Program in virtual machine with shortcut?"
date: 2010-09-13
forum: Virtualisation
---

### Post by halosfan on 2010-09-13
Is there any virtualization software for linux that will allow launch the program in the desired operating system. For example, if I wanted to launch Modelsim XE, I would have to start up windows in the virtual machine then select Modelsim from the start menu. I would like to just click on a shortcut that will automatically launch the program in the virtual machine. Is there any way to do that?

---

### Post by TheFu on 2010-09-14
There was a similar question asked in this forum a few months ago that seemed to provide some hope for the asker.  He wanted to have different programs in different OSes communicate in the way that all the MS-Office products can communicate - - at least that's what my terrible memory recalls today.

My best suggestion is to check out WINE or one of the commercial variants of it.

---

### Post by Rusty au Lait on 2010-09-14
I believe that you can create a startup cmd (a batch file) that will execute upon login. In windows it goes into your startup menu. There's a trick in windows that automatically logins upon booting. Is that what your after?

---

### Post by halosfan on 2010-09-14
I think in Parallels for Mac it will automatically place a shortcut on the Mac doc that will launch the program in the virtual machine. This is what I'd like to do if possible.

Rusty, that might work, but I wouldn't want the same program opening everytime I open the virtual machine.

---

### Post by TheFu on 2010-09-16
> **halosfan said:**
> I think in Parallels for Mac it will automatically place a shortcut on the Mac doc that will launch the program in the virtual machine. This is what I'd like to do if possible.

Rusty, that might work, but I wouldn't want the same program opening everytime I open the virtual machine.

If that is all you want, there's a "seamless app" mode in VirtualBox that may be useful. I'm not a Mac user.

---

### Post by halosfan on 2010-09-16
> **TheFu said:**
> If that is all you want, there's a "seamless app" mode in VirtualBox that may be useful. I'm not a Mac user.

That seamless app mode is amazing! Thanks TheFu. I still would like to know if you can create a shortcut in ubuntu to launch the program in a virtual machine, but if not this is a pretty good substitute.

---

