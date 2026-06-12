---
title: "How to increase the text resolution of the text console(No Xserver installed) ?"
date: 2005-11-10
forum: Server Platforms
---

### Post by Akhran on 2005-11-10
Eg. With the server installation of Ubuntu, which always boot up in runlevel 1, is it possible to increase the screen resolution? I think by default it is in 640 x 480 or 800 x 600 cos the fonts are huge.

Thanks !

---

### Post by tonym on 2005-11-13
Add vga=ask to your kernel boot parameters. When you boot you will then be given various choices for screen layout. When you have found the one you like replace "ask" by the specified value.

Regards

Tony.

---

