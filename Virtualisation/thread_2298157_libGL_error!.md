---
title: "libGL error!"
date: 2015-10-09
forum: Virtualisation
---

### Post by Matias_Persson on 2015-10-09
Hi! I have a very very frustrating error.
I'm programming a game for linux, compiles fine, runs fine... But the console gives errors;

When program is run;
```
pci id for fd 6: 80ee:beef, driver (null)
libGL error: core dri or dri2 extension not found
libGL error: failed to load driver: vboxvideo
pci id for fd 6: 80ee:beef, driver (null)
libGL error: core dri or dri2 extension not found
libGL error: failed to load driver: vboxvideo

```

When program is closed;
```
pci id for fd 6: 80ee:beef, driver (null)
libGL error: core dri or dri2 extension not found
libGL error: failed to load driver: vboxvideo
pci id for fd 6: 80ee:beef, driver (null)
libGL error: core dri or dri2 extension not found
libGL error: failed to load driver: vboxvideo
X error of failed request: BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request: 72 (X_PutImage)
  Resource id in failed request: 0x4800002
  Serial number of failed request: 1291
  Current serial number in output stream: 1294

process returned 1 (0x1)
press ENTER to continue.

```

Now I am sure the program works just fine, but I can't release a program that gives errors in my virtualbox as I would never know if the program would give errors outside of vbox! Imagine I released the game and it spammed errors to the user :p

Any ideas?

---

