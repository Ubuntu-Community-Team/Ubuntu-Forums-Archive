---
title: "REQUEST: Tomboy"
date: 2005-01-19
forum: Ubuntu Backports
---

### Post by ametade on 2005-01-19
Hi everybody,

Would it be possible to add Tomboy to the repository?  I'm having problems with it since I've updated my system with the backport repository.

Thanks.

---

### Post by jdong on 2005-01-19
Backports uses the latest stable Mono release. Make sure you've compiled against this.

As far as Tomboy -- It's more of an extra. I want to taper off backports development, to develop enhancements to the backporting process for Hoary.

---

### Post by frankps on 2005-01-22
I have problems with all Mono apps running on Hoary.

Muine is with out sound.

Tomboy crashes when I click on it's menu (like New Note).

F-spot comes up with an empty application window.

---

### Post by ZakZak on 2005-01-22
[QUOTE=jdong]As far as Tomboy -- It's more of an extra. I want to taper off backports development, to develop enhancements to the backporting process for Hoary.[/QUOTE]

I just installed Tomboy today out of curiousity, but it crashes at startup for me.  I'm guessing this is the same problem ametade described since I'm also running many other backports packages.

Is Tomboy easy to compile from source?  I might just try that...

-Zak

---

### Post by ametade on 2005-01-23
I've solved tomboy's problem by downgrading libgtk-cil to 1.0.2-1 version (using synaptic). I'm trying to make a .deb package for tomboy's last version (0.3.1-1), but I'm having some difficulties building it.

---

### Post by jdong on 2005-01-23
Umm, did you compile that tomboy from source? It seems like it was compiled against an old version of GTK# (libgtk-cil)

---

### Post by ZakZak on 2005-01-23
I just ended up compiling from source myself and it's working fine in tray-icon mode.  I have no idea how to make it work as a panel applet (I'm too new to GNOME, I guess) - "make install" didn't do it, certainly.

Tomboy is pretty cool, though.  Way better than plain xpad or something. :)

-Zak

---

