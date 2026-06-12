---
title: "gnome-devel breakage"
date: 2005-05-15
forum: Ubuntu Backports
---

### Post by Slo Mo Snail on 2005-05-15
Hi,
when using hoary-backports and hoary-extras one can't install gnome-devel anymore because of missing libgnome-menu-dev packages for the version in backports... can somebody upload them?

```
apt-get install gnome-devel
[....]
The following packages have unmet dependencies:
  gnome-devel: Depends: gnome-core-devel (= 62ubuntu2) but it is not going to be installed
E: Broken packages
```

```
apt-get install gnome-core-devel
[....]
The following packages have unmet dependencies:
  gnome-core-devel: Depends: libeel2-dev (>= 2.8.2) but it is not going to be installed
                    Depends: libnautilus-extension-dev but it is not going to be installed or
                             libnautilus2-dev (>= 2.8.2) but it is not installable
E: Broken packages
```

```
apt-get install libeel2-dev
[....]
The following packages have unmet dependencies:
  libeel2-dev: Depends: libgnome-menu-dev (>= 2.9.1) but it is not going to be installed
E: Broken packages
```

```
apt-get install libgnome-menu-dev
[....]
The following packages have unmet dependencies:
  libgnome-menu-dev: Depends: libgnome-menu0 (= 2.10.1-0ubuntu1) but 2.10.1-0ubuntu1+cvs20050425 is to be installed
E: Broken packages
```

---

### Post by jdong on 2005-05-15
This is due to the inclusion of the Menu Editor Project. Please file this report with that project instead, and I'll include his fix. 

[http://ubuntuforums.org/forumdisplay.php?f=67](http://ubuntuforums.org/forumdisplay.php?f=67)

---

### Post by Slo Mo Snail on 2005-05-25
Reported there: [http://ubuntuforums.org/showthread.php?t=34569](http://ubuntuforums.org/showthread.php?t=34569)

jdong, can you tell me where you got the sources of the package? maybe i'll find a way to build the -dev package

---

### Post by jdong on 2005-05-25
They were handed to my by Amaranth

---

