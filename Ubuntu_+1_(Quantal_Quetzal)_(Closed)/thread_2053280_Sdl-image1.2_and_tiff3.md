---
title: "Sdl-image1.2 and tiff3"
date: 2012-09-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-09-05
Yesterday there was a sdl-image1.2 update.

However, the package libsdl-image1.2 still depends on libtiff4.

Now that ubuntu has moved from tiff3 to tiff, also the libsdl-image1.2 should depend on the new libtiff5.

Here:
[https://launchpad.net/ubuntu/quantal/+source/sdl-image1.2/1.2.12-3~exp1](https://launchpad.net/ubuntu/quantal/+source/sdl-image1.2/1.2.12-3~exp1)

---

### Post by Harry33 on 2012-09-07
Now the newest update fixes this issue and libtiff4 can be removed.

[https://launchpad.net/ubuntu/quantal/+source/sdl-image1.2/1.2.12-3~exp1ubuntu1](https://launchpad.net/ubuntu/quantal/+source/sdl-image1.2/1.2.12-3~exp1ubuntu1)

---

### Post by dino99 on 2012-09-07
> **Harry33 said:**
> Now the newest update fixes this issue and libtiff4 can be removed.

[https://launchpad.net/ubuntu/quantal/+source/sdl-image1.2/1.2.12-3~exp1ubuntu1](https://launchpad.net/ubuntu/quantal/+source/sdl-image1.2/1.2.12-3~exp1ubuntu1)

not exactly, wine1.5 still use it.

---

