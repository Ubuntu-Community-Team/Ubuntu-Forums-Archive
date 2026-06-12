---
title: "How do I remove dual boot of Home &amp; Media Center"
date: 2007-02-16
forum: Windows
---

### Post by CheshireMac on 2007-02-16
I have a laptop with the boot option of Home XP and Media Center. In the boot screen, it givesme the option of booting to one or the other, but I only want Media Center with a dual boot to Edgy . . .how do I get rid of the Home XP option?

---

### Post by louis_nichols on 2007-02-16
It's not that easy, I'm afraid.

First of all, the Windows boot manager, not at all surprisingly, can't boot any other OS than windows. So you need to setup grub under edgy (although I'm confused about how you manage to boot into edgy at all - did you not install it yet?). If I remember correctly, grub will automatically setup the boot menu to contain all installed OS's.

After this, not having XP home in the list (although I'm also confused about why you'd want to have an OS on the HDD that you never want to boot into - you could just remove it entirely) is as simply as editing, as root, the file /boot/grub/menu.lst and removing the lines referring to XP home.

---

