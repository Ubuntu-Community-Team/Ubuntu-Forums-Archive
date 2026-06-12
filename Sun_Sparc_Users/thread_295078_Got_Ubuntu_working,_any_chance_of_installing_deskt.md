---
title: "Got Ubuntu working, any chance of installing desktop the offline way?"
date: 2006-11-07
forum: Sun Sparc Users
---

### Post by mahy on 2006-11-07
Hello,

just a few minutes ago i successfully installed Ubuntu on UltraSparc 5. Apart from some googling for advice how to deal with OpenBoot, it was flawless. Then i logged in, put inside a Xubuntu CD (x86) and entered 'sudo apt-cdrom add'. After few seconds' searching the CD, it told me it was unable to find any indexes or whatever, i.e. nothing doing. Is there anything i've done wrong? Is there a way to avoid downloading Xorg, Xfce and many other things AGAIN? Thanks for your answers.

Mahy

---

### Post by netztier on 2006-11-08
> **mahy said:**
> Hello,

just a few minutes ago i successfully installed Ubuntu on UltraSparc 5. Apart from some googling for advice how to deal with OpenBoot, it was flawless. Then i logged in, put inside a Xubuntu CD (x86) and entered 'sudo apt-cdrom add'. After few seconds' searching the CD, it told me it was unable to find any indexes or whatever, i.e. nothing doing. Is there anything i've done wrong? Is there a way to avoid downloading Xorg, Xfce and many other things AGAIN? Thanks for your answers.


The 6.10 Sparc CD is server-only, thus does not contain the packages for xubuntu-desktop, ubuntu-desktop etc.

If you've donwloaded them and their versions in [FONT="Courier New"]**/var/cache/apt/...**[/FONT] are up-to-date, an [FONT="Courier New"]**aptitude install xubuntu-desktop**[/FONT] should only download packages that are more recent than the cached ones - if it's peen preceded by a proper [FONT="Courier New"]**aptitude update**[/FONT], that is.

Ifyou don't have the .deb-packages (and that is *all* of them for your preferred desktop environment, ~500 for ubuntu-desktop, I believe), there's no way around downloading them, one way or the other. If you know exactly how to do it, you might be able to download the whole bunch of packages on another computer, organize them into some repository-like structure on a CD, and then add that CD to the installation sources in your Ultra5's [FONT="Courier New"]**/etc/apt/sources.list**[/FONT], but giving any further help here is beyond my capabilites.

regards

Marc

---

### Post by mahy on 2006-11-08
Alright, in other words, i can't use the packages from Xubuntu i386 installation cd...

---

