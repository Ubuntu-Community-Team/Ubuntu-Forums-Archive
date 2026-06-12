---
title: "broken package"
date: 2013-03-21
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2013-03-21
gnome 1:3.4+7 ubuntu3 is broken on my end. is it just me?

---

### Post by rburkartjo on 2013-03-21
complete error message reads

E: /var/cache/apt/archives/gnome-shell-extensions_3.6.0-0ubuntu1_all.deb: trying to overwrite '/usr/share/gnome-shell/extensions/alternate-tab@gnome-shell-extensions.gcampax.github.com/extension.js', which is also in package alternatetab-ext 0.1~precise

---

### Post by pqwoerituytrueiwoq on 2013-03-21
looks like a packages is being obsoleted but not marked as obsolete, you need to remove the package that has the file it is trying to overwrite

---

### Post by rburkartjo on 2013-03-21
pqw did some more research and looks like i really dont need it so just uninstall package.fixed tks

---

