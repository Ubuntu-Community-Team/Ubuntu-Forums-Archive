---
title: "Shared folder"
date: 2008-04-04
forum: Virtualisation
---

### Post by hanniph on 2008-04-04
I dont know much about virtualization, but Im really thinking about it. Im going to make a virtual windows XP in my Ubuntu installation and I was wondering **if I will be able to make a some kind of a shared folder that both virtualized Xp and Ubuntu could easily reach? **

---

### Post by bodhi.zazen on 2008-04-04
Yes, it is easy in fact. 

IMO the best is to use a network protocol such as samba, nfs, ftp, ssh (scp or sshfs), or http.

Alternately you can use an .iso , cdrom, flash drive, or shared partition "shared folder".

Of the options I suggest samba or nfs.

---

