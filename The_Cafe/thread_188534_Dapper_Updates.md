---
title: "Dapper Updates"
date: 2006-06-04
forum: The Cafe
---

### Post by bruce89 on 2006-06-04
It seems as if there have been some Dapper updates built, but they don't appear in the repositories - [https://launchpad.net/distros/ubuntu/+builds](https://launchpad.net/distros/ubuntu/+builds).  And yes, I do have the Dapper Updates enabled.

---

### Post by tom56 on 2006-06-05
Good point, I haven't received these either. They are mentioned in the new weekly newsletter too - [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue1?action=show&redirect=UbuntuWeeklyNewsletter%2FCurrent](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue1?action=show&redirect=UbuntuWeeklyNewsletter%2FCurrent)

---

### Post by bruce89 on 2006-06-06
Actually, they only appeared to be installable last night, so if you update now, you will get them.  I just wonder why they were delayed a week after they were built before they were released.

---

### Post by patrick295767 on 2006-06-06
[Dapper updates ?]
 Someone knows when the bug/problem associated to **the the processor working at maximum speed will be fixed **??
  
  

[I]
> Points négatifs: 
- **fréquence du processeur bloquée sur sa valeur maximale quelquesoit le mode de gestion de l'alimentation sélectionnée (notamment userspace ondemand et powersave). **- réinstallations de plusieurs paquets après la migration (kubuntu-desktop, imprimante...) 
- pas d'outil de recherche utilisant une base de données comme beagle ou kat. 
- les outils graphiques utilisées en administrateur comme adept, kuser, etc utilisent une sale police. On ne peut pas la changer. [/I]

---

### Post by jdong on 2006-06-06
The mentioned updates have just recently began to pop into the dapper-updates repository. You should be able to get it now.


As far as the processor issue, I'm not sure if that's a relevant problem? Powernowd has always dynamically controlled processor clock fine. Up to a few weeks before the release, there **was** a bug with powernowd only controlling the 1st processor (so multicore processors and SMP setups were affected), but even that was solved before the release.

---

