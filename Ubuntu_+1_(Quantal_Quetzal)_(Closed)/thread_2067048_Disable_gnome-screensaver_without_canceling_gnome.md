---
title: "Disable gnome-screensaver without canceling gnome"
date: 2012-10-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by odror on 2012-10-06
I would like to replace gnome-screensaver with xscreensaver.

When I try to remove gnome-screensaver. It requires removing the meta-package gnome. Is there a way to disable it without removing the gnome package.

Thanks

---

### Post by stinkeye on 2012-10-06
As far as I know removing **gnome** should only remove that package.
> A meta-package is a package that doesn't contain applications within itself, but simply depends upon particular versions of other packages, so that when it is installed, it drags all of them in too. The package manager uses it to know which particular packages to install. For example, the ubuntu-desktop metapackage installs the full GNOME desktop environment, with all the other packages that are in a default Ubuntu install. The existence of meta-packages makes it very easy to install other Ubuntu derivatives on your desktop; see below for more information. 

It is technically just fine to remove a meta-package, if required, and this shouldn't necessarily cause any problems. However, it is strongly recommended that you reinstall that package if you decide to manually upgrade to another version of Ubuntu. The package manager requires those packages to be installed for it to successfully perform the upgrade.
[**_[COLOR="DarkRed"]Meta-packages Explanation[/COLOR]_**]("https://help.ubuntu.com/community/CommonQuestions#Meta-packages:_ubuntu-desktop")

Did you install the gnome desktop because the **gnome** package is not in the default 12.10 Ubuntu install.
Best way to uninstall is use **synaptic** (may need to install), as you can see what is about to be removed.

---

### Post by odror on 2012-10-06
> **stinkeye said:**
> As far as I know removing **gnome** should only remove that package.

[**_[COLOR="DarkRed"]Meta-packages Explanation[/COLOR]_**]("https://help.ubuntu.com/community/CommonQuestions#Meta-packages:_ubuntu-desktop")

Did you install the gnome desktop because the **gnome** package is not in the default 12.10 Ubuntu install.
Best way to uninstall is use **synaptic** (may need to install), as you can see what is about to be removed.

My installation is as close as possible to the default one with some extras.

When I try to remove gnome-screensaver. Synaptic tells that the gnome and gnome-core meta-packages will removed as well. My concern is that If I remove a meta-package my system will not be updating itself with a new package layout as the gnome meta-package changes in the future. Al I want is to disable the gnome-screensaver and use xscreensaver.

---

### Post by stinkeye on 2012-10-06
> **odror said:**
> My installation is as close as possible to the default one with some extras.

When I try to remove gnome-screensaver. Synaptic tells that the gnome and gnome-core meta-packages will removed as well. My concern is that If I remove a meta-package my system will not be updating itself with a new package layout as the gnome meta-package changes in the future. Al I want is to disable the gnome-screensaver and use xscreensaver.
I don't understand this enough to give you an absolutely correct answer so I will have to leave it for someone who does.

---

