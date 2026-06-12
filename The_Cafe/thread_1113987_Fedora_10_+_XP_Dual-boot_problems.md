---
title: "Fedora 10 + XP Dual-boot problems?"
date: 2009-04-02
forum: The Cafe
---

### Post by armageddon08 on 2009-04-02
Hi everybody!
I've F10 installed on my lappy. I wanted to install Windows XP. So, I popped in my XP DVD and booted. The installation screen stuck after the screen which says "Setup is inspecting your hardware". :( So what do I do now ?

---

### Post by armageddon08 on 2009-04-02
Bump........

---

### Post by dmitriyp13 on 2009-04-02
This isnt really answering your question but you could give VirtualBox a try instead of installing XP directly.

---

### Post by armageddon08 on 2009-04-02
> **dmitriyp13 said:**
> This isnt really answering your question but you could give VirtualBox a try instead of installing XP directly.

I don't have enough of RAM to do that(512 megs only).

---

### Post by armageddon08 on 2009-04-03
No help??????

---

### Post by Simian Man on 2009-04-03
Normally for a dual-boot, you'd install Windows first and then Linux.  If it was me, I'd load a live CD and fire up gparted to delete all partitions.  Then install Windows on the whole drive, then reinstall Fedora and use the partitioner there to make space for both.

---

### Post by armageddon08 on 2009-04-03
Does that mean it is not possible to install XP after F10?

---

### Post by swoll1980 on 2009-04-03
> **armageddon08 said:**
> Does that mean it is not possible to install XP after F10?

It's possible, but you have to manually configure the nt loader in Windows, or install grub, and configure it, to be able to chose your OS. You might not have a big enough partition to install it. Maybe?

---

