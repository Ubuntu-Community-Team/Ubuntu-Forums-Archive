---
title: "Ubuntu on Xorg"
date: 2020-01-17
forum: Ubuntu Development Version
---

### Post by P-I H on 2020-01-17
I'm able to login with Ubuntu on Xorg, but my favorite game CIV VI has problems. I'm able to start the game, but the computer hangs when trying to change graph settings. However it works with Wayland login.

---

### Post by dino99 on 2020-01-17
If you are using an intel igpu, then you might hit the 'gpu hang' issue met by numerous users

One of the many: [https://gitlab.freedesktop.org/drm/intel/issues/713](https://gitlab.freedesktop.org/drm/intel/issues/713)

---

### Post by P-I H on 2020-01-17
This is with a Radeon RX 5700 graphic card and it was no problem some days back.

---

### Post by dino99 on 2020-01-17
then check with a new user profile to detect a possible issue with the actual profile.

---

