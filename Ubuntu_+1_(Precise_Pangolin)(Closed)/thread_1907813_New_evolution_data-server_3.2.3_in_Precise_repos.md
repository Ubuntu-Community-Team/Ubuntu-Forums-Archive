---
title: "New evolution data-server 3.2.3 in Precise repos"
date: 2012-01-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-12
The new evolution-data-server (3.2.3-0ubuntu1) is in the Precise repos now.
However, you should not try to install it because of the dependencies of certain other packages,
like gnome-panel and gnome-shell or thse will get uninstalled.

The names of the packages libebook1.2-12,  libecal1.2-10 and libedataserver1,2-15 have changed.
This is the reason for incompatibility.

---

### Post by Harry33 on 2012-01-12
This dependency problem has now been fixed with correct updates of gnome-panel and gnome-shell, also in Ricotz Testing PPA.
Thanks!

---

### Post by dino99 on 2012-01-12
I'm not using ricotz ppa at all, and have installed the Evolution upgrade: in fact empathy needs to be purged first, then the Evolution upgrade can be made, and finally reinstall Empathy, no trouble :)

---

