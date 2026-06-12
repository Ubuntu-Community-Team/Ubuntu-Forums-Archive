---
title: "Deleted sources.list"
date: 2016-07-16
forum: Ubuntu Phone and Tablet
---

### Post by obroden on 2016-07-16
I accidentely deleted my sources.list-file. Can anyone who runs ubuntu touch post your sources.list-file so I can copy. I currently run OTA-11 on a BQ m10.

Best regards,

Oskar

---

### Post by krusty8 on 2016-07-16
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports/ vivid main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ vivid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ vivid-updates main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ vivid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ vivid universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ vivid universe
deb http://ports.ubuntu.com/ubuntu-ports/ vivid-updates universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ vivid-updates universe

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it 
## newer versions of some applications which may provide useful fe
## Also, please note that software in backports WILL NOT receive a
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ vivid-backports main r
# deb-src http://ports.ubuntu.com/ubuntu-ports/ vivid-backports ma

deb http://ports.ubuntu.com/ubuntu-ports/ vivid-security main rest
deb-src http://ports.ubuntu.com/ubuntu-ports/ vivid-security main 
deb http://ports.ubuntu.com/ubuntu-ports/ vivid-security universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ vivid-security unive
# deb http://ports.ubuntu.com/ubuntu-ports/ vivid-security multive
# deb-src http://ports.ubuntu.com/ubuntu-ports/ vivid-security mul

```

---

### Post by krusty8 on 2016-07-16
Nexus 7 2013, based on a very old devel release for this device, but I think the sources list shouldnt really change in between. However, unless you use apt, I wouldn't expect that it matters whether you have that file or not

---

