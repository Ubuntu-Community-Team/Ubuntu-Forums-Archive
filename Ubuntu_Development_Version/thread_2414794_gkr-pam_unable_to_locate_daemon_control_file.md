---
title: "gkr-pam: unable to locate daemon control file"
date: 2019-03-15
forum: Ubuntu Development Version
---

### Post by fthx on 2019-03-15
Hi,

After I suspend my laptop, Evolution is unable to get the online accounts credentials. Is it known ?

---

### Post by fthx on 2019-03-15
it seems to be related to a bug against resume from suspend after a 2nd monitor use : the resume goes to gdm instead of the usual screen.

---

### Post by Smask on 2019-03-15
Do you having proposed enabled?


Me, I have some issues with suspend at the moment because they are moving everything Gnome from 3.31.9 to 3.32 at the moment. They haven't updated GOA yet.

---

### Post by fthx on 2019-03-15
Yes, that's what I watch :
[http://ftp.gnome.org/pub/gnome/sources/gnome-online-accounts/](http://ftp.gnome.org/pub/gnome/sources/gnome-online-accounts/)
But clearly, there is something else involved here, in my case.

---

### Post by fthx on 2019-03-18
[https://bbs.archlinux.org/viewtopic.php?id=244965](https://bbs.archlinux.org/viewtopic.php?id=244965)

---

### Post by dino99 on 2019-03-18
Same as [https://ubuntuforums.org/showthread.php?t=2414197](https://ubuntuforums.org/showthread.php?t=2414197)

---

### Post by fthx on 2019-03-22
[https://bbs.archlinux.org/viewtopic.php?id=245097](https://bbs.archlinux.org/viewtopic.php?id=245097)
and commit :
[https://git.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/gtk3&id=b3a2d479833895cf7de34be9df63c18e79f72034](https://git.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/gtk3&id=b3a2d479833895cf7de34be9df63c18e79f72034)

---

