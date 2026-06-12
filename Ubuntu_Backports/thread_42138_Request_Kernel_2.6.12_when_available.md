---
title: "Request: Kernel 2.6.12 when available ?"
date: 2005-06-16
forum: Ubuntu Backports
---

### Post by DarkSilver on 2005-06-16
Hello,

Just to know if the next stable version of the kernel (2.6.12) will be backported when it'll be released.

thx.

---

### Post by jdong on 2005-06-16
I've only done one kernel backport, and that was for Warty. It was such a painful and disgusting job that I'd never want to do it again. Backporting kernels is not a smart idea.

---

### Post by DarkSilver on 2005-06-16
I really don't understand why !!!!

Tjhe linux image package :
Depends: initrd-tools (>= 0.1.75ubuntu2), coreutils | fileutils (>= 4.0), module-init-tools (>= 0.9.13)

So there won"t be problems of dependances...
I can't see what is the modifications between a kernel for Breezy and for Hoary...

In my mind, I though that just install the breezy package will work in Hoary, because there's no dependencies problems...

---

### Post by jdong on 2005-06-16
It's not just dependencies. It's binary compatibility. Every restricted module needs to be recompiled, and most of those will have an upward ring of dependencies.

Also, experimental kernels (yes -- new Breezy kernels ARE of this nature) are  filled with new or updated patches that Hoary simply isn't designed to work with. The end result is instability. In addition, I'm one person, not a security team. I won't be able to respond to kernel security flaws as effectively or responsively as the Ubuntu security team can.

If you want a new kernel, you're best off doing it yourself. I cannot put all 25,000 Backports users through this, when for most of them their kernel is working fine.


If you want another reason, the upstream kernel maintainer (Fabbione) has asked me not to backport kernels.

---

### Post by denzilla on 2005-06-22
Will Breezy use the newest kernel released?

---

### Post by XDevHald on 2005-06-22
[QUOTE=denzilla]Will Breezy use the newest kernel released?[/QUOTE]
 Not exactly sure just yet, someone might run me over and get this before I do in the morning, but I wouldn't think they'd add it.

Also the new gnome version is 2.11.3, of course myself, I am missing out on atleast 2-3 weeks of Ubuntu/Gnome Updates so I am not exactly sure of what is exactly happening due to lack of online and to much work outside of online :D

---

### Post by sjmorgan on 2005-06-23
Correct me if I'm wrong but isn't backports specifically for application updates? I mean wtf is the point of using Hoary if you're going to ask for backports of stuff like the kernel, just use Breezy!

---

### Post by McQuaid on 2005-06-23
Alittle OT, but what patches are applied to the hoary kernel?  When I first discovered ubuntu I thought it was a stock kernel, then I read it's patched with inotify.  Anything else?

---

### Post by jdong on 2005-06-23
[QUOTE=McQuaid]Alittle OT, but what patches are applied to the hoary kernel?  When I first discovered ubuntu I thought it was a stock kernel, then I read it's patched with inotify.  Anything else?[/QUOTE]

Check out linux-patch-ubuntu-2.6.10

---

### Post by dodongo on 2005-06-23
Compiling a new kernel from scratch is a great exercise (so long as it's in the same 2.x branch!).  If nothing else, it'll fill you in on how quickly and efficiently everything can break when one key dependency isn't filled properly :)

But seriously, if you do take the time to do it, I'm sure you'll learn a lot.  Just going through the configuration GUIs and learning about all the different features you can manipulate within the kernel is a really eye-opening experience.

---

