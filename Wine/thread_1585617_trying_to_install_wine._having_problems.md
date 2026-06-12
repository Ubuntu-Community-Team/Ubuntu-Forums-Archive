---
title: "trying to install wine. having problems"
date: 2010-09-30
forum: Wine
---

### Post by imtired111 on 2010-09-30
I am trying to install wine on my computer running ubuntu 9.4. i am trying to install from a flash drive and when i click to install it opens the package installer, reads the package, and then an error message pops up and it wont let me install wine. can someone help me?:confused:

---

### Post by dino99 on 2010-10-01
if you dont show us the exact message, how we can know it ?

the easiest way to install wine (the latest), is to add this ppa to your synaptic repo tab:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

then update, upgrade

---

### Post by Soulcage on 2010-10-01
Sounds like the problem you're having is that you don't have all the files. The list I saved is:

cabextract gnome-exe-thumbnailer icoutils lib32nss-mdns ttf-mscorefonts-installer ttf-symbol-replacement-wine1.3 winbind wine1.3-gecko wine1.3 winetricks wisotool

There might even be some more I installed as dependancies for other programs. Also after those are installed theres a list of font packages that are usually automatically installed that I didn't bother saving.
They were downloaded from sourceforge.

(I'm assuming you didn't download the source code.)

---

