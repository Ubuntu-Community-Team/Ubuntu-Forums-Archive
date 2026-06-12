---
title: "No vsync with geforce 840m"
date: 2014-10-04
forum: Ubuntu Development Version
---

### Post by startas on 2014-10-04
So, i'm using ubuntu 14.10 with newest nvidia drivers 340.46 and there is no vsync anywhere, no vsync in desktop, no vsync in games, and games are running super fast, its imposible to do anything. Is there any fix to try ? I have geforce 840m.

---

### Post by startas on 2014-10-04
Also same tearing with drivers 343.22 .

---

### Post by mc4man on 2014-10-04
I'd assume 840m mean optimus. If so - 
Use on-board intel instead
Use bumblebee instead of nvidia-prime (then lack of vsync may only be when using bumblebee or maybe bumblebee is ok?

---

### Post by startas on 2014-10-06
No, i want to use only geforce, i dont need intel graphics.

---

### Post by mc4man on 2014-10-06
In regards to nvidia-prime - 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1260128](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1260128)

---

