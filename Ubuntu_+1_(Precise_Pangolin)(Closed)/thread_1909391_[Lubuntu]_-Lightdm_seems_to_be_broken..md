---
title: "[Lubuntu] -Lightdm seems to be broken."
date: 2012-01-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MG&amp;TL on 2012-01-15
After installing yesterday's build of Lubuntu 12.04, the login manager seems to be dead (an infinite loop before login, Ctrl-Alt-F1-6 broken). I managed to fix this by installing lxdm by chrooting as described [_ here_ ]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=6#doc_chap1") although obviously, modified for *buntu.

Not sure if this helps anyone.

Also, where do I file a bug, and is there one already?

---

### Post by dino99 on 2012-01-15
into a terminal:

ubuntu-bug lightdm
(needs to have a launchpad account)

but, is lightdm-gtk-greeter installed ?

---

### Post by ventrical on 2012-01-15
> **MG&TL said:**
> After installing yesterday's build of Lubuntu 12.04, the login manager seems to be dead (an infinite loop before login, Ctrl-Alt-F1-6 broken). I managed to fix this by installing lxdm by chrooting as described [_ here_ ]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=6#doc_chap1") although obviously, modified for *buntu.

Not sure if this helps anyone.

Also, where do I file a bug, and is there one already?

 What I do is just download <lubuntu-desktop> from the repos on some of the 12.04 installs I have. works great !

---

### Post by MG&amp;TL on 2012-01-15
yup, thanks guys, bug dutifully reported. :)

@ventrical;interesting for my other pc; this one won't run ubuntu. Thanks!

---

### Post by ventrical on 2012-01-15
> **MG&TL said:**
> yup, thanks guys, bug dutifully reported. :)

@ventrical;interesting for my other pc; this one won't run ubuntu. Thanks!

 I just use synaptic .. same thing with xubuntu-desktop and cairo-dock.

---

### Post by MG&amp;TL on 2012-01-15
> **ventrical said:**
> I just use synaptic .. same thing with xubuntu-desktop and cairo-dock.

Sorry, not quite sure what your preferences in package manager have to do with that...although me too. :D Care to explain for a sleepy moi?

---

