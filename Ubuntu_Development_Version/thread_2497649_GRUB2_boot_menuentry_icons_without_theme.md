---
title: "GRUB2 boot menuentry icons without theme"
date: 2024-05-13
forum: Ubuntu Development Version
---

### Post by rolfbruge on 2024-05-13
Does Ubuntu's version of GRUB2 support adding menuentry icons in a standard grub menu without using a theme?

Have not been able to find specific info on adding a custom icon to display with the menuentries on a non-themed GRUB2.

Is this possible, and if so,  how exactly can this be done?

---

### Post by oldfred on 2024-05-13
Have not seen it.
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

But grub is both a boot loader and a boot manager/menu.
You can use rEFInd as boot manager which has ICONs, if you have an UEFI system.
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

