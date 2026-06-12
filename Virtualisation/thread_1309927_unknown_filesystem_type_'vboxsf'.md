---
title: "unknown filesystem type 'vboxsf'"
date: 2009-11-01
forum: Virtualisation
---

### Post by small_potato on 2009-11-01
I have been trying to run windows xp on ubuntu 9.10 through virtualbox. When I tried to create a shared folder, I got an error message "unknown filesystem type 'vboxsf'". I installed the guest addition on windows xp, and I set the shared folder in virtualbox. Did I miss anything? Thank you.

---

### Post by lmarmisa on 2010-11-23
> **small_potato said:**
> I have been trying to run windows xp on ubuntu 9.10 through virtualbox. When I tried to create a shared folder, I got an error message "unknown filesystem type 'vboxsf'". I installed the guest addition on windows xp, and I set the shared folder in virtualbox. Did I miss anything? Thank you.

Filesystem vboxsf only applies when Ubuntu is running as a guest system.

But your guest system is XP. In this case, open "My Network Places" -> "Entire Network" -> "VirtualBox Shared Floders" -> \\Vboxsvr and finally you will locate there the shared folder(s).

---

