---
title: "Stack Smashing Protection in Xubuntu or Lubuntu?"
date: 2014-07-31
forum: Security
---

### Post by ubusr on 2014-07-31
Do the Xubuntu or Lubuntu distributions have stack smashing
protection enabled in their compiled binaries?

I know Ubuntu has it.  But given X/Lubuntu focus on space/speed
perhaps they don't enable it?  Or perhaps it is in packages
shared with Ubuntu like Firefox but not unique packages like Xfce?

More generally, are there security feature differences between the
3 distributions?

Thanks.

---

### Post by JKyleOKC on 2014-08-01
They all use the same kernel, so the odds are that they all have the same kernel features. However if the protection is provided in the window manager itself (not very likely) then all three would be different...

---

### Post by bashiergui on 2014-08-02
Look here to see the differences and similarities between the flavors
You'll note (as jkyle said) they're all built on the same base and pull from the same repositories
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

So this applies to all the flavors
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

---

### Post by ubusr on 2014-08-02
Thanks.  I'm interested in knowing if the applications (as well as the kernel) have the protection, particularly the browser, but also the other desktop apps and the window manager.  I think SSP is a compile time option for each binary.  I don't think running the same kernel or building from the same source necessarily means the apps would have SSP enabled.  Something like Firefox might or might not have it depending on whether X/Lubuntu share Ubuntu's binaries or whether they compile them themselves.  Some things in the desktop environment would be unique to X/Lubuntu.  Since SSP increases the binary size and slows performance its seems possible they might not enable it?   

The Security/Features page doesn't mention remixes specifically.  It does say: "Ubuntu's compiler hardening applies not only to its official builds but also anything built on Ubuntu using its compiler."  The question would be do X/Lubuntu use Ubuntu's compiler/options in the case of building all their apps and kernel.  Synaptic seems to says Xfce4 and LXDE packages come from Universe.  So its not clear to me what is protected and what isn't.

---

### Post by bashiergui on 2014-08-02
All the software for each flavor comes from the same repository. Therefore they're all compiled the same. As for whether all software has it enabled, according to the link I gave you:

"gcc's -fstack-protector provides a randomized stack canary that protects against stack overflows, and reduces the chances of arbitrary code execution via controlling return address destinations. Enabled at compile-time. (*A small number of applications do not play well with it, and have it disabled.*) The routines used for stack checking are actually part of glibc, but gcc is patched to enable linking against those routines by default"

---

