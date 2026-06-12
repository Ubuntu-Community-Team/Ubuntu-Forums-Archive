---
title: "Irssi install"
date: 2006-05-21
forum: Server Platforms
---

### Post by rensu on 2006-05-21
Could someone tell me what's wrong with my apt-get or sources.list? When im trying to install irssi im getting this error: irssi-text: Depends: libperl5.8 (>= 5.8.7) but it is not going to be installed

What could be wrong ?:S And if im trying to install libperl5.8 getting this:
libperl5.8: Depends: perl-base (= 5.8.7-5ubuntu1) but 5.8.7-5ubuntu1.2 is to be installed

---

### Post by rensu on 2006-05-21
Nevermind I just found the solution:
Had to comment the cdrom line in sources.list and change hoary to breezy.

---

