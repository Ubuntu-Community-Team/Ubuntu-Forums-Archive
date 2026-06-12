---
title: "sudo aptitude install edubuntu"
date: 2006-09-24
forum: The Cafe
---

### Post by phersotty on 2006-09-24
Hi,

My current system is a triple boot of Ubuntu/xp/Suse.  I thought I would try out Edubuntu 64.  From what I have read about Edubuntu, its basically Ubuntu with preinstalled educational packages. After the install I logged in and got a blank brown screen and a mouse cursor that I can move around the screen.  I imagine its an xorg tweak, but it made me think why should I bother troubleshooting this installation when I already have a functional Ubuntu system installed.  Another thing I found interesting about Edubuntu is that it uses a text installer when one of its target audiences is children.  I wouldn't necessarily expect that children would be doing the install, but often children are more computer savvy than their parents who would probably be doing the install.  My point then, is that the install for Edubuntu, in my opinion should be so easy that a child could do it.  I found Ubuntu to be far simpler to install than Edubuntu which brings me to the following conclusion.  Instead of maintaining a separate parallel distro wouldn't it would be better to  create an Edubuntu repository instead that could be accessed from Ubuntu with a command like sudo aptitude install edubuntu?

---

### Post by towsonu2003 on 2006-09-24
> **phersotty said:**
> Hi,

My current system is a triple boot of Ubuntu/xp/Suse.  I thought I would try out Edubuntu 64.  From what I have read about Edubuntu, its basically Ubuntu with preinstalled educational packages.
you can try it with your ubuntu install. ```

sudo aptitude install edubuntu-desktop # to install
sudo aptitude remove edubuntu-desktop # to uninstall
```
> After the install I logged in and got a blank brown screen and a mouse cursor that I can move around the screen.  I imagine its an xorg tweak, but it made me think why should I bother troubleshooting this installation when I already have a functional Ubuntu system installed.
you can copy over your working xorg.conf from ubuntu to edubuntu (and restart X)

> Another thing I found interesting about Edubuntu is that it uses a text installer when one of its target audiences is children.
the audience, afaik, is schools. schools (it dept of a school, or a savvy teacher) are supposed to install it, teachers are supposed to administer it, and students + teachers are supposed to use it interactively via thin clients.

---

### Post by phersotty on 2006-09-25
:cool: edubuntu-desktop :mrgreen: 

Yeah, so I would like to take back everything I said about the whole installing edubuntu from within ubuntu thing.  You'd think I would have tried that since I've also installed kubuntu-desktop and xubuntu-desktop.  

Thanks for the advice and the clarification on who Edubuntu's audience is.

---

### Post by towsonu2003 on 2006-09-25
you're most welcome :mrgreen:

---

