---
title: "[proposed] Dont upgrade whoopsie"
date: 2018-02-28
forum: Ubuntu Development Version
---

### Post by dino99 on 2018-02-28
The whoopsie into proposed have switched to libcurl4; which fully break network-manager due to libcurl3 removal.
Its a show breaker. Waiting for libcurl4-gnutls & network-manager supporting that new libcurl4.](*,)
lp:1752319

---

### Post by dino99 on 2018-03-01
A reboot was required to solve that problem :p

---

### Post by zika on 2018-03-01
Opera-developer is broken by this upgrade and Opera is not installable due to```
opera : Depends: gstreamer0.10-plugins-good but it is not installable
```...
Just for those addicted to Opera, I'm not...

---

