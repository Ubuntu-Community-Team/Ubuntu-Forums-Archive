---
title: "Gdm (3.8.1.1) in Saucy - dependencies"
date: 2013-06-07
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-06-07
Gdm has been rebuilt 4 times in a short period very recently.
But no attention was given to the fact that it still depends on dconf-tools, which is nowadays a transitional package.
It only has a meaning to help installing the two new (split) packages dconf-cli and dconf-editor.

Gdm should not depend on dconf-tools, but instead on dconf-editor.

---

### Post by jbicha on 2013-06-07
This isn't the bug tracker. ;)

---

### Post by shaun79 on 2013-06-09
I've created a bug report! Bug #1189169

---

### Post by Harry33 on 2013-06-10
> **shaun79 said:**
> I've created a bug report! Bug #1189169

Thanks,
Jeremys says, however, gdm needs only dconf-cli.
So we will wait for a new gdm build.

Also the meta package "ubuntu-gnome-desktop" depends on dconf-editor, so both split packages are needed.

---

