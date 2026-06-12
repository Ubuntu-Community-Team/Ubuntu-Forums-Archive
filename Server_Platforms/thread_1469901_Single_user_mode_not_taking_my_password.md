---
title: "Single user mode not taking my password"
date: 2010-05-02
forum: Server Platforms
---

### Post by wesg on 2010-05-02
I want to fix my disks with fsck but using sudo init 1 is not allowing me in. It shuts my services down, then gives a "Give root password for maintenance" prompt. I've tried my password, but it rejects it. 

What can I do?

---

### Post by Naitsirhc Hsem on 2010-05-02
you can change the root password in System > administration > users and groups.

---

### Post by wesg on 2010-05-02
Should probably mention that I'm running the server version... I don't think this version even has a GRUB menu to boot, does it?

---

### Post by lisati on 2010-05-02
> **Naitsirhc Hsem said:**
> you can change the root password in System > administration > users and groups.
The server version doesn't install a GUI by default, unless the user chooses to add one in later.
Please also read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **wesg said:**
> Should probably mention that I'm running the server version... I don't think this version even has a GRUB menu to boot, does it?
If you're using 9.10 and later, there is a grub menu available by holding down "shift" at startup.

---

