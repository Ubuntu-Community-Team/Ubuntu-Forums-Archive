---
title: "Is there any tutorial about how to create a debian package?"
date: 2005-07-09
forum: Ubuntu Backports
---

### Post by tzutolin on 2005-07-09
Hello everyone,

I would like to make some debian package and share them here, but I'm a newbie on debian package creation. Could someone tell me how to do this? Thanks!

---

### Post by Seth on 2005-07-09
[QUOTE=tzutolin]Hello everyone,

I would like to make some debian package and share them here, but I'm a newbie on debian package creation. Could someone tell me how to do this? Thanks![/QUOTE]
 The granddaddy of all Debian maintainer docs: the New Maintainer's Guide.

[http://www.debian.org/doc/maint-guide/ch-start.en.html](http://www.debian.org/doc/maint-guide/ch-start.en.html)

---

### Post by tzutolin on 2005-07-09
Thanks Seth. That's a great resource. Thank you!

Oh, BTW, your blog looks great :-)

---

### Post by Velvet Elvis on 2005-07-09
Thanks.

For some reason using checkinstall feels disrespectful to the debian packaging system.  I'm a recent convert from slackware.  I was too anal for gentoo so I'm used to compiling bleeding edge packages from source as soon as they come out and keeping up with deps using pencil and paper.  Slackware dropped gnome support, so I'm here.  I'll be glad to contribute whatever I come up with once I get this figured out.

---

### Post by Seth on 2005-07-10
[QUOTE=Velvet Elvis]Thanks.

For some reason using checkinstall feels disrespectful to the debian packaging system.  I'm a recent convert from slackware.  I was too anal for gentoo so I'm used to compiling bleeding edge packages from source as soon as they come out and keeping up with deps using pencil and paper.  Slackware dropped gnome support, so I'm here.  I'll be glad to contribute whatever I come up with once I get this figured out.[/QUOTE]
 Checkinstall is only for "personal" debs, as they're specific to your system. It's a quick-and-dirty way to not have to worry about things you build from source. Much better to use something like pbuilder to build debs for distribution.

---

