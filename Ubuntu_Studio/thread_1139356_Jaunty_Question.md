---
title: "Jaunty Question"
date: 2009-04-27
forum: Ubuntu Studio
---

### Post by vaughnm on 2009-04-27
Does Jaunty have a RT kernel for low latency recordings?

---

### Post by Stochastic on 2009-04-27
Yes.  Some people have been experiencing some system freezing with it though.

---

### Post by vaughnm on 2009-04-27
if i upgrade to jaunty will the Rt kernel install or will I need to compile/upgrade it seperately?

---

### Post by Stochastic on 2009-04-27
If you install the ubuntustudio-audio meta package it will install the linux-rt package.  I have no idea if your system has the ubuntustudio-audio package installed currently (or for that matter the linux-rt package), but if it does, then a simple upgrade will take care of that installation.  If not, then you simply need to apt-get either one of those packages to get the RT kernel.

---

