---
title: "gtk-gnutella necesita ayuda"
date: 2011-06-16
forum: Software
---

### Post by mama21mama on 2011-06-16
Probando clientes Bittorrent/p2p di con gtk-gnutella, me pareció bastante maduro el proyecto y anda muy bien.

Conozco Frostwire (usa java), giFToxic, MLDonkey, y aMule... lo que note con los demás clientes es que gtk-gnutella pide colaboración.

[[IMG]http://twitpic.com/show/thumb/5c9mvs.png[/IMG]]("http://twitpic.com/5c9mvs")

Aquí mi granito de arena dando a conocer este pedido y paso la ultima versión estable en DEB.

Claro compilada por mi en mi Lubuntu 11.04
19,6 MB [http://mamalibre.no-ip.org/gtk-gnutella_0.96.9-0_i386_lubuntu.deb](http://mamalibre.no-ip.org/gtk-gnutella_0.96.9-0_i386_lubuntu.deb)
md5sum: 1062b55f17c819dc2bd1c70dd8730b31

---

### Post by josecuervo86 on 2011-06-16
gtk-gnutella esta en los repos..

---

### Post by mama21mama on 2011-06-16
pero esta versión?
[http://packages.ubuntu.com/search?keywords=gtk-gnutella](http://packages.ubuntu.com/search?keywords=gtk-gnutella)
solo la 0.96.8

el DEB es el 0.96.9 stable

---

### Post by josecuervo86 on 2011-06-17
pero hay algun cambio importante? Solo llege a ver hasta 0.96 jeje

---

### Post by mama21mama on 2011-06-17
A mi no me conectaba a los nodos la versión de los repos en 11.04
Por eso hice el DEB.

> gtk-gnutella (0.96.9-0) unstable; urgency=medium

  * New upstream yearly release.

 -- Raphael Manfredi <Raphael_Manfredi@pobox.com>  Sun, 13 Mar 2011 21:08:44 +0000

gtk-gnutella (0.96.8-0) unstable; urgency=medium

  * New upstream release, fixing critical bugs in 0.96.7.

 -- Raphael Manfredi <Raphael_Manfredi@pobox.com>  Sun, 21 Mar 2010 09:34:26 +0000

gtk-gnutella (0.96.7-0) unstable; urgency=medium

  * New upstream release.

 -- Raphael Manfredi <Raphael_Manfredi@pobox.com>  Sat,  6 Mar 2010 19:55:23 +0000

gtk-gnutella (0.96.6-0) unstable; urgency=medium

  * New upstream release.

 -- Raphael Manfredi <Raphael_Manfredi@pobox.com>  Sun, 29 Mar 2009 15:19:56 +0000

gtk-gnutella (0.96.6~unstable) unstable; urgency=low

  * Unstable release for testing

 -- Christian Biere <christianbiere@gmx.de>  Thu, 10 Apr 2008 15:03:02 +0000

gtk-gnutella (0.96.5-0) unstable; urgency=medium

  * New upstream release

 -- Christian Biere <christianbiere@gmx.de>  Tue,  1 Apr 2008 21:05:33 +0000

gtk-gnutella (0.96.5~unstable) unstable; urgency=low

  * Unstable release for testing

 -- Christian Biere <christianbiere@gmx.de>  Sat,  9 Jul 2007 00:30:02 +0200

gtk-gnutella (0.96.4-0) unstable; urgency=medium

  * New upstream release

 -- Christian Biere <christianbiere@gmx.de>  Sat,  7 Jul 2007 04:30:02 +0200

gtk-gnutella (0.96.4~unstable) unstable; urgency=low

  * Unstable release for testing

 -- Christian Biere <christianbiere@gmx.de>  Sun, 26 Nov 2006 15:00:45 +0100

gtk-gnutella (0.96.3-0) unstable; urgency=medium

  * New upstream release

 -- Christian Biere <christianbiere@gmx.de>  Thu,  9 Nov 2006 22:10:48 +0100

gtk-gnutella (0.96.2-0) unstable; urgency=medium

  * New upstream release

 -- Christian Biere <christianbiere@gmx.de>  Mon, 16 Oct 2006 21:06:00 +0100

gtk-gnutella (0.96.1-0) unstable; urgency=medium

  * New upstream release

 -- Raphael Manfredi <Raphael_Manfredi@pobox.com>  Wed, 22 Feb 2006 17:14:17 +0100

gtk-gnutella (0.96cvs200602040801-2) unstable; urgency=medium

  * Urgency medium to get this out in the field quickly

 -- Anand Kumria <wildfire@progsoc.org>  Mon,  6 Feb 2006 11:11:48 +1100

gtk-gnutella (0.96cvs200602040801-1) unstable; urgency=low

  * Merge with latest 0.96 and some fixes from CVS (Closes: #350358)
  * Remove xlibs Build-Dep (Closes: #346677)
  * Activate D-BUS support
  * Update Spam and hostiles and ultra host lists
  * A few IPv6 bug fixes

 -- Anand Kumria <wildfire@progsoc.org>  Mon,  6 Feb 2006 03:02:29 +1100

gtk-gnutella (0.96-0) unstable; urgency=medium

  * New upstream release

 -- Raphael Manfredi <Raphael_Manfredi@pobox.com>  Tue, 24 Jan 2006 22:14:17 +0100

gtk-gnutella (0.96b-2) unstable; urgency=low

  * Convert to using debhelper rather than debmake

 -- Anand Kumria <wildfire@progsoc.org>  Sun,  5 Feb 2006 13:07:36 +1100

gtk-gnutella (0.96b-1) unstable; urgency=medium

  * New upstream release
  * TLS and IPv6 support
  * Ability to browse hosts
  * Fix "Bitzi Metadata" issue, asking for it will add the column and
    make it a minimum size (Closes: #327188)
  * Implement saving/restoring of default search order (Closes: #327194)
  * de.po changes have been included upstream (Closes: #313758)
  * Urgency set to medium since all current versions of gtk-gnutella have
    expired

 -- Anand Kumria <wildfire@progsoc.org>  Sat, 26 Nov 2005 11:

Solo un extracto del Changelog

---

