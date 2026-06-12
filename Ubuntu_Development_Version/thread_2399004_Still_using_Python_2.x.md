---
title: "Still using Python 2.x"
date: 2018-08-20
forum: Ubuntu Development Version
---

### Post by TenPlus1 on 2018-08-20
We are almost on 18.10 and some of the packages in the repositories are still using Python 2.x instead of being migrated to 3.x so we can finally remove Python2.7 from the dependencies.

calibre
calibre-bin
gvfs-backends
libsmbclient
mpv
samba-libs
minetest (this doesnt even use python2, why is it a dependency ???)

---

### Post by mc4man on 2018-08-20
What's the big deal about python (i.e python2.7) It's not going away for some time, it's not on the default image, so what??
(- mpv  never depended on python, in 18.10 it has a recommend of youtube-dl which has a depend on python3. Users of the upstream youtube-dl would want to have python installed as that's what the youtube-dl script uses. (unless they want to edit the script to use python3..

There are many other useful packages that need python2.7-minimal, either directly or thru dependencies so get over the nonsense..

---

### Post by jbicha on 2018-08-20
Actually, python2 is still part of the Ubuntu Desktop default install because of gvfs-backends which depends on libsmbclient which depends on samba-libs. samba still uses python2.

A minimal Ubuntu Server install (meaning without OpenStack) won't include python2.

The Bionic release notes are confusing on this issue and could probably use some additional explanation.

---

### Post by TenPlus1 on 2018-08-21
mc4man: I'm not averse to things using python, am simply stating that in this day and age it would be nice if they started using python 3.x instead.

---

