---
title: "splashy help"
date: 2008-10-04
forum: The Cafe
---

### Post by bravoall1552 on 2008-10-04
:confused::cry:Can someone help me with splashy! I tried installing it on a Linux from SCratch system, but it isn't working. I already checked init.d and that's working, but that's about it. Help?

---

### Post by Inteluxe on 2008-10-07
You need to do: update-initramfs -u -t -k 'uname -r'
also make sure you add vga=791 in the /boot/grub/menu.lst at the end on the the kernel line that loads the Ubuntu.

---

