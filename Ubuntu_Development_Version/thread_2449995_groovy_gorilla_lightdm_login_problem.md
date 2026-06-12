---
title: "groovy gorilla lightdm login problem"
date: 2020-09-05
forum: Ubuntu Development Version
---

### Post by rajeshnk131275 on 2020-09-05
after updating to groovy gorilla can't login in lightdm but kde plasma works

---

### Post by Cheltspy on 2020-09-05
gdm3 is also broken along with ubuntu-desktop(not supporting gnome 3.37.90) and apport.

removing apport(disabling it is not enough) brings gdm3 and gnome back up without ubuntu mods.

---

### Post by Cheltspy on 2020-09-13
ubuntu-desktop and ubuntu-desktop-minimal now have just one broken dependency gvfs-bin

Actually, gnome 3 works very well without ubuntu mods and seems faster.

---

### Post by cecilpierce on 2020-09-13
Installed lightdm, auto login works.

---

