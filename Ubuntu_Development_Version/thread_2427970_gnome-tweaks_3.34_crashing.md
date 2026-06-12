---
title: "gnome-tweaks 3.34 crashing"
date: 2019-09-27
forum: Ubuntu Development Version
---

### Post by dino99 on 2019-09-27
PythonArgs: ['/usr/bin/gnome-tweaks']
Traceback:
 Traceback (most recent call last):
   File "/usr/bin/gnome-tweaks", line 15, in <module>
     gi.require_version("Handy", "0.0")
   File "/usr/lib/python3/dist-packages/gi/__init__.py", line 129, in require_version
     raise ValueError('Namespace %s not available' % namespace)
 ValueError: Namespace Handy not available

[https://bugs.launchpad.net/ubuntu/+source/gnome-tweaks/+bug/1845754](https://bugs.launchpad.net/ubuntu/+source/gnome-tweaks/+bug/1845754)

---

### Post by leego2 on 2019-09-28
Running **sudo apt install libhandy-0.0-dev** fixed it for me

---

### Post by dino99 on 2019-09-28
Good catch :P
but this also install a bunch of other 'dev' packages, which are not expected; better to fix gnome-tweaks compilation.

---

### Post by kansasnoob on 2019-09-28
Thanks for reporting. I just noticed the same thing so marked it effecting me too and subscribed.

---

### Post by dino99 on 2019-09-28
In fact there is no need of libhandy-0.0.dev (and its enless other 'dev' packages list), but simply installing 'gir1.2-handy-0.0' to get it working as expected.  :P

---

### Post by dino99 on 2019-09-28
Has been fixed with the latest 3.34.0-2 version.

---

