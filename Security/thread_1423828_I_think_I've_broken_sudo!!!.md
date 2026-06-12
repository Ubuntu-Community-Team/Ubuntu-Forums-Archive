---
title: "I think I've broken sudo!!!"
date: 2010-03-07
forum: Security
---

### Post by CyberJacob on 2010-03-07
in a rage of anger against vi i decided to open my firewall config file in gedit, made some changes and was then confrunted by the fact that it was read only. i decided to change the permissions for the whole of the /etc folder with:
```
sudo chmod 777 /etc/*
```this also changed /etc/sudoers so that now whenever I try to use sudo i get the error:
> sudo: /etc/sudoers is 0777, should be 0440
segmentation faulti cannot change it back to 440 because i need sudo to do that. PLEASE HELP

---

### Post by CharlesA on 2010-03-07
Boot into a recovery shell from the GRUB menu and change the permissions to what they were from there.

Just wanted to note: If you are editing anything that is not in yer home directory, you probably will only have read access to it, You need to use sudo or gksu to have full rights to whatever file you want to edit.

---

### Post by CyberJacob on 2010-03-07
> **CharlesA said:**
> Boot into a recovery shell from GRUB
How do I do that, and what's gksu?

---

### Post by CharlesA on 2010-03-07
> **CyberJacob said:**
> How do I do that, and what's gksu?

gksu = graphical sudo. It's used for running graphical apps instead of sudo.

Try holding down shift while the machine is booting.

---

### Post by CyberJacob on 2010-03-07
done it, thanks. OHNO:o
this thing just leads from one thing to another, ah well, time to start another thread.

---

