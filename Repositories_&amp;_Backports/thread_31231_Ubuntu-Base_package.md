---
title: "Ubuntu-Base package"
date: 2005-05-02
forum: Repositories &amp; Backports
---

### Post by sys on 2005-05-02
Hi I just found that I have to remove the 'ubuntu-base' package, cause I removed some packages on which it depends (jfsutils etc.).

What annoys me:

[I]The Ubuntu base system
This package depends on all of the packages in the Ubuntu base system.

It is safe to remove this package if some of the base system packages are not
desired.  However, it is recommended that you keep it installed, because it is
used to carry out certain upgrade transitions (such as adding new packages to
the system).[/I]

What are "certain Upgrade-transistions"? Do I need this package to upgrade from hoary to breezy for example?

greetings
fabian

---

### Post by Leif on 2005-05-02
Simply, yes.

---

### Post by sys on 2005-05-02
Hm, so there's no way of removing packages I don't need without destroying my possibility to update?

---

### Post by Leif on 2005-05-02
No, it's not a problem. When the time for upgrade comes, select ubuntu-base and ubuntu-desktop, click upgrade all, and then go and deselect whatever you don't want.

---

