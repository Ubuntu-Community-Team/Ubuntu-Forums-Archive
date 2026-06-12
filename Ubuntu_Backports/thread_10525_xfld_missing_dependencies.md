---
title: "xfld missing dependencies"
date: 2005-01-09
forum: Ubuntu Backports
---

### Post by rbrimhall on 2005-01-09
Hi,
I just tried to install the xfld package and it failed with this error:

xfld-desktop:
 Depends: xnetcardconfig (>=0.1.1) but it is not installable
 Depends: xfce4-taskbar-plugin  but it is not installable

---

### Post by jdong on 2005-01-09
xnetcardconfig is in Staging. Taskbar plugin ... hmm, will research on that.

Work around that  by installing xfce4, then everything ontop of that by hand.

---

### Post by rbrimhall on 2005-01-09
The wierd thing is that I swear I installed this a couple of weeks ago but then removed it to install the RC3 using the installers...

---

