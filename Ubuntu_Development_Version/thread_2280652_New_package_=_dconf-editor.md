---
title: "New package = dconf-editor"
date: 2015-06-01
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-06-01
Just a heads up, it used to be that we'd install 'dconf-tools' but it's now a dummy package:

> DConf is a low-level key/value database designed for storing desktop
environment settings.

This package is a transitional package installing dconf-cli and dconf-editor,
it can safely be removed

We now have 'dconf-editor':

> dconf-editor (3.16.1-1) unstable; urgency=medium

  * Upload to unstable.
  * New upstream release.
  * Point Vcs-* to the unstable branch.
  * Point Homepage to the dconf project wiki page.
  * Bump debhelper compatibility level to 9.
  * Fix debian/copyright to comply with version 1.0 of the spec.
  * Update Build-Depends as per configure.ac.

 -- Michael Biebl <biebl@debian.org>  Wed, 27 May 2015 01:59:42 +0200

dconf-editor (3.16.0-1) experimental; urgency=medium

  * **[COLOR="#FF0000"]Initial release[/COLOR]**.

 -- Iain Lane <laney@debian.org>  Mon, 13 Apr 2015 17:33:31 +0100


---

### Post by Bashing-om on 2015-06-01
@kansasnoob; Hello (!);

Thanks for the heads up . noted.

[INDENT][INDENT]the times they are achang'n
[/INDENT][/INDENT]

---

