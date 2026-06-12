---
title: "Samba upgrade during Ubuntu upgrade from 8.04.4 LTS to 10.04 LTS"
date: 2010-05-10
forum: Server Platforms
---

### Post by snpz on 2010-05-10
Hi!
I have a network with ~40 workstations (basically XP) and a couple of Ubuntu Linux (8.04.4 LTS) servers. First of them is working as domain controller with LDAP backend and second as file server for user and departament shares.
Right now everything runs perfect, except Win7 support, so i'm considering of upgrading both servers to next LTS release - 10.04. For tests some months ago i upgraded samba using [this ]("http://www.jeremycole.com/blog/2009/12/01/upgrade-samba-3-0-28a-to-3-4-3-on-ubuntu-8-04-lts/") manual on both servers. In result couldnt log into domain and couldnt reach shares (used old conf files)! Problem solved when installed back samba 3.0.28a from repositories.
Right now i'm not sure i whant to upgrade my servers till i'm not confident, that everything will work as on 8.04. Could anyone describe me some details on changes with samba that i should deal with during upgrade?!

---

