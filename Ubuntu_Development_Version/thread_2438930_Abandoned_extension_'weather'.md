---
title: "Abandoned extension 'weather'"
date: 2020-03-20
forum: Ubuntu Development Version
---

### Post by dino99 on 2020-03-20
The ex registered page now return 404 error (chromium 80)
[https://github.com/jenslody/gnome-shell-extension-openweather](https://github.com/jenslody/gnome-shell-extension-openweather)

Needs to find a cloned extension that works with gnome-shell 3.36

---

### Post by P-I H on 2020-03-20
Now I'm on Fedora 32 with Gnome 3.36 and Openweather works almost OK.
This link is working
[https://gitlab.com/jenslody/gnome-shell-extension-openweather](https://gitlab.com/jenslody/gnome-shell-extension-openweather)

Only one problem settings isn't working. There are also problems with settings in other extensions like Dash to panel.

---

### Post by kurt18947 on 2020-03-21
Open Weather by jens installs okay for me but as P-I H says I can't set locations. It does appear to be a settings problem because extensions that don't require settings seem to work properly. For example 'Lock Keys' and 'Add Username to Top Panel' work as expected but those don't require any user input. If I click on 'Extensions' and 'all versons' there are 122 pages of extensions. If I click on 'current version' there are no extensions listed. It does not appear to be individual extensions that are the problem.

---

### Post by dino99 on 2020-03-21
Error logged:
Error: uuid "@uuid@" from metadata.json does not match directory name "openweather-extension@jenslody.de"

---

