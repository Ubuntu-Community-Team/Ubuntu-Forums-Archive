---
title: "Unity crashed in Ubuntu 12.04 beta 2"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by robgraves on 2012-04-16
I recently installed Ubuntu 12.04 beta 2 on my desktop and it was working fine for a few days and just now when i booted up, when i try to log into Unity, i get the wallpaper, but the taskbar and dash never load, i'm currently in kde on that same system.  Has anyone else encountered this problem or know of a solution to this?

---

### Post by ventrical on 2012-04-16
Have you tried to load it in Unity 2D ?

---

### Post by robgraves on 2012-04-16
no, but i just had something weird happen, this is from a kde session, based on another thread, i ran:
```
unity --reset
```
from the kde desktop and now my desktop looks like this:

lol, any ideas?

---

### Post by robgraves on 2012-04-16
update: after a logout, unity 3D is working as it should, but now kde is borked, it won't load at all.

---

### Post by robgraves on 2012-04-16
alright, I resolved the problem by running:
```

sudo apt-get autoremove kde-full
sudo apt-get install kde-full

```
now I just don't know what caused the issue originally, but the problem's fixed.

---

