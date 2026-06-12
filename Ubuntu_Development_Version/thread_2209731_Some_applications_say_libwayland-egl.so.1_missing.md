---
title: "Some applications say libwayland-egl.so.1 missing"
date: 2014-03-07
forum: Ubuntu Development Version
---

### Post by wgarcia on 2014-03-07
In my Trusty installation, if I enter "cheese" in the terminal I get:

cheese: error while loading shared libraries: libwayland-egl.so.1: cannot open shared object file: No such file or directory

totem is giving me the same

Anybody else? I haven't seen any bug reported on this (I reported one on totem [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1288875](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1288875)).

---

### Post by wgarcia on 2014-03-07
Looking around in Launchpad I found 

[https://bugs.launchpad.net/kubuntu-ppa/+bug/1206371](https://bugs.launchpad.net/kubuntu-ppa/+bug/1206371)

Basically the same was happening with kwin in an upgrade from 13.04 to 13.10. The following workaround worked for me:

```
sudo ln -s /usr/lib/x86_64-linux-gnu/mesa-egl/libwayland-egl.so.1 /usr/lib/libwayland-egl.so.1
```

---

### Post by mc4man on 2014-03-07
In an Ubuntu install this would have been the result of of having libhybris installed which there is no good reason to have unless you want unity8 or ubuntu-touch installed

---

### Post by wgarcia on 2014-03-07
Yes, I installed unity8 to try the preview, since it's a feature for 14.04 to offer this preview this issue should be addressed anyway as it's something that more people will stumble upon.

---

### Post by mc4man on 2014-03-07
What's interesting (maybe) is if you switch /usr/lib/x86_64-linux-gnu/libhybris-egl/ld.so.conf from auto to manual for libhybris-egl/ld.so.conf, (#1),  then there seems to be no issue, even if then switching back to auto (as in screen, no symlink was created
```
sudo update-alternatives --config  x86_64-linux-gnu_egl_conf
```

---

