---
title: "non-free code in default install?"
date: 2005-04-05
forum: The Cafe
---

### Post by emmanuel on 2005-04-05
Hello,

This post is more a question. Today hoary wanted to upgrade my "linux-restricted-modules" (mentionning among others winmodems support) and "nvidia-kernel-common".
now i would like to keep a free linux on my computer, only free software code. firmwares are OK. What are those modules? are they "non-free" because of firmwares or because of non-GPL code?

what annoys me is that linux-386 depends on those packages so if i uninstall them, i can't be sure anymore to have safe upgrades (to have the complete kernel).

so, do i have non-GPL code live on my system, and if yes how to remove it without potentially breaking ugprade? free software by default was a big argument for ubuntu for me.

Thank you!

emmanuel

---

### Post by az on 2005-04-05
"What are those modules? are they "non-free" because of firmwares or because of non-GPL code?"

They are non-gpl because they consist of brecompiled binaries.  If you do not have the hardware, you do not need them.  Does linux-image-2.6 depend on the restricted modules.  There are several linux-image metapackages.  I think there is a way to remove them and still get your updates.

It is great to have a distribution that makes it easy to have only free software on your system.

---

### Post by emmanuel on 2005-04-05
I'll extend my question: if there are non-free packages *in the default install*, what are they, and is there a way to be _sure_ my system is pure free software?
my problem is, i can remove that, hopefully it won't break system upgrade, but are there others besides that..

i'm a bit disapointed that ubuntu doesn't seem to be free by default :-(

emmanuel

---

### Post by HungSquirrel on 2005-04-05
It IS free by default, because linux-restricted-modules is not a default package (at least, it wasn't with Warty).

There are tons of packages that are non-GPL but are still free by the way.  GPL isn't the only free license.  ;)

---

### Post by az on 2005-04-05
"GPL isn't the only free license"

Right, but you can have something under a "free" licence that does not really protect your freedom.  To make it simple, debian uses the Debian free software guideline.

[http://www.debian.org/social_contract](http://www.debian.org/social_contract)

Ubuntu main adheres to the debian free software guidelines.  Just use the main archive.

Linux-restricted modules is the only non-free stuff that is included in the installer.  Everyting in main is free.  Keep universe, restricted and multiverse disabled and you should be okay.

---

