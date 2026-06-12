---
title: "HowTo install SuperTux ?!?"
date: 2010-05-10
forum: Ubuntu Studio
---

### Post by bobromeo on 2010-05-10
Newbie question from a 1st time user of Studio (10.4) after 5 years of Edubuntu. I'm missing my installer. Should I install adept or am I missing something ?

---

### Post by diamondnular on 2010-05-10
Should it be just as simple as using the following command:
```
$ sudo apt-get install supertux
```
I have never tried Edubuntu, so no idea about adept (which also can be installed easily by *sudo apt-get install adept*, but I do believe all Ubuntu derivaties should have apt-get.

---

### Post by cchhrriiss121212 on 2010-05-10
You are not missing anything, adept is the KDE (desktop environment) package manager, but Ubuntu uses Gnome (a different desktop environment) which has Synaptic package manager in the System menu.

---

### Post by ronnielsen1 on 2010-05-10
Do you not have a package manager? Synaptic?

---

### Post by bobromeo on 2010-05-11
I see that it is possible to install SuperTux with synaptic, before I used it only to install whole packages, not for single programs/applications

The last 5 years I used this:
[https://help.ubuntu.com/community/InstallingSoftware#for%20Ubuntu/Xubuntu/Edubuntu%20:%20%22Add/Remove%22](https://help.ubuntu.com/community/InstallingSoftware#for%20Ubuntu/Xubuntu/Edubuntu%20:%20%22Add/Remove%22)

I installed adept, but it wasn't this program, it was a lot of KDE, so I removed it.

Q1: Who knows the 'install' name of the program mentioned in the link above ?

Q2: Why is it left out of Studio ?

I think it is a user friendly installer.

---

### Post by ronnielsen1 on 2010-05-11
> Q1: Who knows the 'install' name of the program mentioned in the link above ?

> **for Kubuntu : Adept**



> Why is it left out of Studio ?

> I installed adept, but it wasn't this program, it was a lot of KDE, 

It may have been an earlier version but still adept

---

### Post by diamondnular on 2010-05-11
> **bobromeo said:**
> I see that it is possible to install SuperTux with synaptic, before I used it only to install whole packages, not for single programs/applications

The last 5 years I used this:
[https://help.ubuntu.com/community/InstallingSoftware#for%20Ubuntu/Xubuntu/Edubuntu%20:%20%22Add/Remove%22](https://help.ubuntu.com/community/InstallingSoftware#for%20Ubuntu/Xubuntu/Edubuntu%20:%20%22Add/Remove%22)

I installed adept, but it wasn't this program, it was a lot of KDE, so I removed it.

Q1: Who knows the 'install' name of the program mentioned in the link above ?

Q2: Why is it left out of Studio ?

I think it is a user friendly installer.
You may want to try software center (sudo apt-get install software-center). It provides similar way of installing/searching for software.

---

### Post by bobromeo on 2010-05-11
@diamondnular: thx, it's at least a look-a-like ;)
What I also like about this program, that it's easy to see what's installed.

@ronnielsen1: I think that Adept is the KDE equivalent of Synaptic.

---

### Post by ronnielsen1 on 2010-05-12
> @ronnielsen1: I think that Adept is the KDE equivalent of Synaptic.

I realize that. I was answering his question. I was tring to explain that while you can have adept in ubuntu, it will pull in a lot of kde libs

---

