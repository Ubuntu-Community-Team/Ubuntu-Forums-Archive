---
title: "Nautilus reverted to version 3.14 !"
date: 2016-02-04
forum: Ubuntu Development Version
---

### Post by fthx on 2016-02-04
In proposed ATM :

nautilus (**1:3.18.4.is.3.14.3-0ubuntu1**) xenial; urgency=medium

  * **Revert to the previous serie**, the new one is going to need more work
    which is not going to be done this cycle (some issues/regressions are
    being handled upstream in 3.20 but we can do that update with our GTK
    version, also the new copy dialog is a bit much of a change and upstream
    confirms it's creating problems that they try to address with more UI
    changes) (lp: [#1541954]("https://launchpad.net/bugs/1541954"))

  [ Marco Trevisan (Treviño) ]
  * debian/patches/ubuntu_open_new_window_for_folders.patch:
    - Open folders in new nautilus windows by default (LP: [#1524721]("https://launchpad.net/bugs/1524721"))

 -- Sebastien Bacher <email address hidden>  Thu, 04 Feb 2016 18:41:31 +0100

---

### Post by grahammechanical on 2016-02-04
It will postpone all moans & accusations that Ubuntu has changed things yet again.

---

### Post by mc4man on 2016-02-04
Good choice,  was keeping 3.14 going here for personal use so happy to see they've realized how poor 3.18 was,  particularly  in an ubuntu session

---

