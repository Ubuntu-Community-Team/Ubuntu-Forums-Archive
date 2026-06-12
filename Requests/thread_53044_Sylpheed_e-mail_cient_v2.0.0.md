---
title: "Sylpheed e-mail cient v2.0.0"
date: 2005-07-30
forum: Requests
---

### Post by SickTwist on 2005-07-30
Sylpheed 2.0.0 was just released and now uses GTK2!  It would be great to see this in the backports repository if at all possible.

---

### Post by kb00heda on 2005-07-30
I would also like to see Sylpheed 2 in Ubuntu! 

However, it has yet to enter Breezy (a quick look at the Ubuntu packages gave version 1.0.4 for Breezy). In other words, if I have understood matters correctly, the new version of Sylpheed thus cannot be backported?

At present I am using "sylpheed-gtk2" instead, which, as revealed by its name, also has GTK2.

---

### Post by TravisNewman on 2005-07-30
unless it goes into extras, that is.
 
We could try to get MOTU to bring it into Breezy. Is it going to be in Debian?

---

### Post by SickTwist on 2005-08-06
Sylpheed 2.0.0 is in Debian unstable.  I tried installing the Debian version in Hoary but there are some unresolveable dependencies. However if I force it to install it seems to run ok.

---

### Post by uggy on 2005-08-07
[QUOTE=SickTwist]Sylpheed 2.0.0 is in Debian unstable.  I tried installing the Debian version in Hoary but there are some unresolveable dependencies. However if I force it to install it seems to run ok.[/QUOTE]
 I installed the unstable Sylpheed2 deb file from Debian Unstable as suggested by SickTwist..
Sylpheed2 seems to work properly... but how di you fix the unresolveable dependencies that appear when I try to apt-get upgrade for exemple. ?

If i try to fix by running apt-get -f install, Sylpheed2 is removed..


Sorry it's french but I think you could understand..
> yannick@yop:  ~  $ sudo apt-get upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Vous pouvez lancer « apt-get -f install » pour corriger ces problèmes.
Les paquets suivants contiennent des dépendances non satisfaites :
  sylpheed: Dépend: libc6 (>= 2.3.2.ds1-21) mais 2.3.2.ds1-20ubuntu13 est installé
            Dépend: libgpg-error0 (>= 1.1) mais 1.0-1 est installé
            Dépend: libpango1.0-0 (>= 1.8.2) mais 1.8.1-0ubuntu2 est installé
            Dépend: sylpheed-i18n (= 2.0.0-1) mais il n'est pas installé
E: Dépendances manquantes. Essayez d'utiliser l'option -f.

---

### Post by SickTwist on 2005-08-16
I downloaded the following packages to my home directory from packages.debian.org:
[list]
[*]sylpheed_2.0.0-1_i386.deb
[*]sylpheed-i18n_2.0.0-1_all.deb
[/list]

I had all of the other dependencies already installed. (Although I have the Hoary version of everything except for the above two packages).

Then I did the following command in my home directory:
```
sudo dpkg --force-depends -i sylpheed*
```
dpkg will list the errors but continue to install Sylpheed anyway.

I think that the packager used incorrect version numbers when listing the dependencies in the deb but maybe I just haven't noticed that something is broken.   :?   As far as I can tell though, Sylpheed runs perfect*

*Caveat:  If I run apt-get after this it complains about broken packages and forces me to uninstall Sylpheed when trying to do upgrades or other installations.  However, I can always re-install Sylpheed doing the above command if I would like.

---

### Post by uggy on 2005-08-19
[QUOTE=SickTwist]
*Caveat:  If I run apt-get after this it complains about broken packages and forces me to uninstall Sylpheed when trying to do upgrades or other installations.  However, I can always re-install Sylpheed doing the above command if I would like.[/QUOTE]

That's exactly my problem...
It's borring to have to uninstall sylpheed, install the new app and re-install again sylpheed each time...  :? 
Nobody know a way to fix this ?

---

