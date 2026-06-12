---
title: "I can't apt-get the Microsoft Core Fonts package"
date: 2005-06-20
forum: Repositories &amp; Backports
---

### Post by tsagas on 2005-06-20
Hi,

I use Ubuntu 5.04. I've enabled all the available Ubuntu repositories through Synaptic, but I can't find this specific package, in order to install it. I searched the keywords; mssttfonts, msttcorefonts, microsoft fonts. In Ubuntu 4.10 I hadn't experienced such a problem.

Any ideas?
Thanks in advance.

--
Dimitris

---

### Post by xristos on 2005-06-20
Geia sou Dimitri !

Check this out ---> [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

I think the one you need is : 
## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by jdong on 2005-06-20
No; it's not in Backports... restricted or multiverse, I think.


Can you post your /etc/apt/sources.list?

---

### Post by az on 2005-06-20
I think it is in the regular multiverse.  You do not need backports for msttcorefonts.


Edit -  Yup:
[http://packages.ubuntu.com/hoary/x11/msttcorefonts](http://packages.ubuntu.com/hoary/x11/msttcorefonts)

---

### Post by tsagas on 2005-06-20
Regular multiverse did the trick.

Thanks guys  :-P 

<greek>Geia sou kai sena xristo kai fxaristw.</greek>

--
Dimitris

---

