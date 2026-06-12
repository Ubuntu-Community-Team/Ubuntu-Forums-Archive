---
title: "gnome-menus (3.31.4-2ubuntu1)  appmenu is now gone"
date: 2019-01-22
forum: Ubuntu Development Version
---

### Post by dino99 on 2019-01-22
Recent gnome-menus (3.31.4-2ubuntu1) upgrade has removed the applications menu on the top left bar  ](*,)

The changelog says:   Fix app menus not updating correctly after app install or removal

---

### Post by mc4man on 2019-01-22
present & working fine here, no use of -proposed on this install

---

### Post by davidmohammed on 2019-01-24
That version of gnome-menus also breaks Ubuntu Budgie - bug report here [https://bugs.launchpad.net/ubuntu/+source/gnome-menus/+bug/1812908](https://bugs.launchpad.net/ubuntu/+source/gnome-menus/+bug/1812908)

Haven't delved in to the gnome-menus patches yet to see what is breaking Budgie ... if anyone has any ideas please shout!

---

### Post by dino99 on 2019-01-24
Might be the faulty package:  gnome-shell-extension-appindicator . Checking Tweaks extension, that one is broken and deactivated now.

Extension "apps-menu@gnome-shell-extensions.gcampax.github.com" had error: GLib.MarkupError: Error on line 241 char 10: Element &#8220;Menu&#8221; was closed, but the currently open element is &#8220;Exclude&#8221;

[https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/156](https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/156)

---

### Post by dino99 on 2019-01-25
Problem solved by that upgrade:

gnome-menus (3.31.4-2ubuntu2) disco; urgency=medium

  * Cherry-pick layout-fix-missing-Exclude-close-tag.patch
    - Fix missing tag that caused problems for traditional menu users
      (Closes: #920226)

 -- Jeremy Bicha <jbicha@debian.org>  Thu, 24 Jan 2019 15:24:54 -0500

---

