---
title: "error gpg"
date: 2016-01-06
forum: Ubuntu Development Version
---

### Post by valereguerin on 2016-01-06
Hello community !

WARNING: /lib/x86_64-linux-gnu/libgpg-error.so.0.17.0 is needed, but cannot be mapped to a package

thanks for regards,):P


Xenial Xerus 16.04 gnome-desktop

---

### Post by zika on 2016-01-06
```
:/lib/x86_64-linux-gnu$ ls -l libgpg*
libgpg-error.so.0 -> libgpg-error.so.0.17.0
libgpg-error.so.0.17.0
```Package is libgpg-error.

---

### Post by valereguerin on 2016-01-06
freeman@Sniper-one:~$  sudo apt-get install libgpg-error.so.0.17.0
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet libgpg-error.so.0.17.0
E: Couldn't find any package by glob 'libgpg-error.so.0.17.0'
E: Impossible de trouver de paquet correspondant à l'expression rationnelle « libgpg-error.so.0.17.0 »
freeman@Sniper-one:~$ 
freeman@Sniper-one:~$ ls -l libgpg*
ls: impossible d'accéder à libgpg*: Aucun fichier ou dossier de ce type
freeman@Sniper-one:~$ sudo apt-get install libgpg-error
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet libgpg-error


in synaptic i have (installed !) : libgpg-error0 ; libgpg-error-dev ; libgpg-error0:i386

i'm ubuntu addict too....

---

### Post by mc4man on 2016-01-06
> **valereguerin said:**
> Hello community !

WARNING: /lib/x86_64-linux-gnu/libgpg-error.so.0.17.0 is needed, but cannot be mapped to a package

thanks for regards,):P

Xenial Xerus 16.04 gnome-desktop

Is there some context to that WARNING:, as is means nothing, do note warnings are usually not errors

---

### Post by zika on 2016-01-07
That is 386 macihe since You have 386 edition of a package installed?
Try```
sudo apt-get install -f
```to see what is missing.
Put output in code-tags so we could read it easily...
```
[COLOR=#000000]E: Impossible de trouver le paquet libgpg-error
```

[/COLOR]

---

### Post by valereguerin on 2016-01-07
i already try 

```
sudo apt-get install -f ; update ; upgrade with terminal with synaptique with aptitude full-upgrade clean autoclean autoremove purge ; dpkg commande purge config files ...
```

 but i have many software and all my paquets are not upgrade yet  ...i try all this commandes every day twice third each day

PS: sorry howefield for the size i thought you could see better !:rolleyes: i use zoom (woks fine !) and i see distorder details with this size format !


ubuntu user since 10.10 before unity.....i use terminal since 2008....and my bookmarks too many links like this :

[COLOR=#0000cd]http://www.tecmint.com/useful-basic-commands-of-apt-get-and-apt-cache-for-package-management/[/COLOR]

[COLOR=#0000ff]http://www.cyberciti.biz/ref/apt-dpkg-ref.html[/COLOR]

my Ubuntu"S"/Cubuntu 14.04 12.04 16.04 are on top each day....Ubuntu addict and loving it TOO, today it's a passion (up 60 install)developp branch since 12.04/12.10/13.04/13.10/14.04.14.10/15.04/15.10>                      That is 386 macihe since You have 386 edition of a package installed?
Try i don't know i'm not sure

????is it possible to have an internet navigator in recovery mode ?????because i can't use man it's...*@%/*+/"#.... désolé....

---

