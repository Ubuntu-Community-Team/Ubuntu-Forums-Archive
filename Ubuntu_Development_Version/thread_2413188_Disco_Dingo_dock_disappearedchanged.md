---
title: "Disco Dingo dock disappeared/changed"
date: 2019-02-22
forum: Ubuntu Development Version
---

### Post by corradoventu on 2019-02-22
After last updates the dock is no longer displayed unless i click on 'Activities' top left on the screen. Also when it appears it has a different appearance.

---

### Post by jbicha on 2019-02-22
The Ubuntu Dock extension was updated for gnome-shell 3.31.90 which has not migrated out of -proposed yet. I expect the new gnome-shell version to land by early next week.

---

### Post by jbicha on 2019-02-22
I see it's entangled with the glibc transition so hopefully that won't take too long.

---

### Post by P-I H on 2019-02-23
I had this problem too, but after I enabled the Developer option and updated the dock is back.
Now I have only the [COLOR=#000000]gnome-keyring bug [/COLOR][LP: #1817128]("https://launchpad.net/bugs/1817128") and a package kit crash, that isn't possible to report.

---

