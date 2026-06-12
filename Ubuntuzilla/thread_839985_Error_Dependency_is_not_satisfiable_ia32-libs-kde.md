---
title: "Error: Dependency is not satisfiable: ia32-libs-kde"
date: 2008-06-24
forum: Ubuntuzilla
---

### Post by bigteks on 2008-06-24
I am running hardy amd64. I followed the install instructions, downloaded the amd64 version of the script today from sourceforge (ubuntuzilla-4.4.9-0ubuntu1-amd64.deb) and double-clicked it. I got this error in the package installer:

Error: Dependency is not satisfiable: ia32-libs-kde

Why does it want kde libraries for ubuntu and if it does, why would the dependency be unsatisfiable?

I did the apt-get install of ia32-libs* & lib32asound2 lib32ncurses5 lib32stdc++6, and got "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded" on both.

Thanks,
Steve

---

### Post by nanotube on 2008-06-25
hi,

well, i don't have a 64bit system to test on... so i just put all the 32bit compatibility libraries there are as dependency, to make sure mozilla's 32bit build of firefox runs ok. 

in ubuntu prior to hardy, ia32-libs-kde existed, but apparently in hardy it does not...

could please you try the attached ubuntuzilla amd64 deb (it has this dependency removed), see if it installs. if it installs, use it to install mozilla's build of firefox, see if it runs ok?

---

### Post by bigteks on 2008-06-25
Thanks, that worked!

---

### Post by Ryklou on 2008-06-25
you should Mark this thread solved.

TY

---

### Post by nanotube on 2008-06-25
> **bigteks said:**
> Thanks, that worked!

excellent!
i'm about to make a new release fixing another buglet, i'll include this fix in it. thanks for your feedback! :)

---

