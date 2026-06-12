---
title: "Is GRUB a necessary piece of software?"
date: 2008-05-15
forum: The Cafe
---

### Post by Luke has no name on 2008-05-15
If I am only installing one OS on one disk, do I need GRUB? 

When I install FreeBSD, it asks if I want to have GRUB installed on my MBR, hard drive, or not at all. When I choose not at all, the OS still boots fine.

Is this true for Linux as well? Could I just as well not have GRUB if I don't need to dual boot?

---

### Post by p_quarles on 2008-05-15
You don't need GRUB, but you need *a* bootloader. There are others that work just fine. GRUB is a nice and relatively easy-to-use tool for booting multiple OSes, but it's not built-in to anything.

---

### Post by Npl on 2008-05-15
If you intend on using (K)Ubuntu, then you will have an easier time using GRUB. Kernel-Updates automatically update the grub-configuration - if you dont have GRUB, but some other Bootloader (aint working without) then you will have to manually tell it to load the new Kernel.

PS. you can disable the GRUB-Menu at boot altogether, so its not like it you should care much for what Bootloader you are using

---

### Post by p_quarles on 2008-05-15
> **Npl said:**
> If you intend on using (K)Ubuntu, then you will have an easier time using GRUB. Kernel-Updates automatically update the grub-configuration - if you dont have GRUB, but some other Bootloader (aint working without) then you will have to manually tell it to load the new Kernel.

PS. you can disable the GRUB-Menu at boot altogether, so its not like it you should care much for what Bootloader you are using
Debian's kernel management system will automatically update LILO as well.

EDIT: And, of course, Debian's system is used by downstream distros such as Ubuntu, as well.

---

