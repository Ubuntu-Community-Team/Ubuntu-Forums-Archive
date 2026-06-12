---
title: "Docky"
date: 2019-09-22
forum: Ubuntu Development Version
---

### Post by kvn-mcmns on 2019-09-22
Why can't i install Docky in Xubuntu.

---

### Post by deadflowr on 2019-09-22
Which version of Xubuntu?
And how are you trying to install it,
and what happens when you try?

---

### Post by kvn-mcmns on 2019-09-22
19.10 Tried to install Docky,Gksu,Numix-folders but nothing worked but in my main computer MXlinux i installed everything just found the deb files and installed them.

---

### Post by kvn-mcmns on 2019-09-22
Also docky gksu numix-folders & palemoon conky manager are not even in the software centre or synaptic.

---

### Post by howefield on 2019-09-22
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by VMC on 2019-09-22
> **kvn-mcmns said:**
> 19.10 Tried to install Docky,Gksu,Numix-folders but nothing worked but in my main computer MXlinux i installed everything just found the deb files and installed them.
"nothing worked" doesn't help us much here, also don't confuse us more referring to another OS. By the way Docky is a better fit for Gnome. Plank is what I use for Xubuntu. Works flawlessly. But if you like the extra stuff, then how did you install it? Maybe try terminal and copy paste failed results.

---

### Post by uRock on 2019-09-22
Not sure if the OP is trying to install by some other means, but this is what happens when I try to install those in Xubuntu 19.10. I ran updates before running this. I just ran this for the OP's sake. I don't want, nor need those in Xubuntu.
```
sudo apt install docky gksu numix-folders
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gksu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package docky
E: Package 'gksu' has no installation candidate
E: Unable to locate package numix-folders

```OP, if you're trying via another method, then do feel free to tell us what you're trying.

---

### Post by uRock on 2019-09-22
I also tried installing via the PPA, but there's no release file yet for eoan. This is the kind of thing I'd expect with a developmental release.

---

### Post by deadflowr on 2019-09-22
gksu has been gone for years now.

docky was last in Ubuntu repository in 18.10.

I see no such package in the repository for numix-folders.
Though there are several numix packages such as numix-gtk-theme and numix-icon-theme.

Palemoon and conky manager have never been in Ubuntu's repositories.

---

### Post by uRock on 2019-09-22
> **deadflowr said:**
> gksu has been gone for years now.

docky was last in Ubuntu repository in 18.10.

I see no such package in the repository for numix-folders.
Though there are several numix packages such as numix-gtk-theme and numix-icon-theme.

Palemoon and conky manager have never been in Ubuntu's repositories.

gksu is the only one of those packages I've ever used. I think the biggest issue for the OP is expecting the dev version to work OOTB without obstacles. My recommendation would be to install 18.04, then build it up to preference.

---

### Post by mc4man on 2019-09-23
Docky is long dead, 4+ years. The last .deb produced was for 15.10, it was copied over thru 18.10
While if you wanted to jump thru some hoops you could actually install it in 19.10, but it"s not going to run, ever..
So find something else like plank or use 18.04 where it may work..

---

