---
title: "apt-get purge question"
date: 2015-07-11
forum: Virtualisation
---

### Post by cybergalvez on 2015-07-11
Stupid question, I saw in a thread that to upgrade virtualbox5 it was recommended that you did a apt-get purge virtualvox4. I know that this should remove all the system level configuration files, but will it leave my VM's alone or remove them too? Also if I use synaptic and select "completely remove" that is the same thing as using purge right?

---

### Post by Vladlenin5000 on 2015-07-11
It will leave your VMs alone because they're neither part of the package nor configuration files. You'll have to import them to the newly (re)installed Virtualbox though.

---

### Post by Bucky Ball on 2015-07-12
*Thread moved to **Virtualisation**.*

---

### Post by cybergalvez on 2015-07-12
Thanks Appreciate the validation

---

