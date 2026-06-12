---
title: "FTP Backports Mirror?"
date: 2005-11-21
forum: Ubuntu Backports
---

### Post by intangible on 2005-11-21
Is there a FTP mirror of the mirrormax source?  I do some work from behind a "semi-transparent" HTTP proxy and I try to use FTP for all my apt sources (makes life a lot easier instead of having to input correct auth information every time for the http proxy).

Thanks for the work.

---

### Post by angrykeyboarder on 2005-11-22
[quote=intangible]Is there a FTP mirror of the mirrormax source? I do some work from behind a "semi-transparent" HTTP proxy and I try to use FTP for all my apt sources (makes life a lot easier instead of having to input correct auth information every time for the http proxy).

Thanks for the work.[/quote]

Do you mean "extras" or "backports". Because backports is no longer on Mirrormax anyway.

---

### Post by intangible on 2005-11-23
Extras, sorry bout that.

---

### Post by angrykeyboarder on 2005-11-25
[quote=intangible]Extras, sorry bout that.[/quote] 
OK, well in that case...

Here's one on the opposite part of the planet (and it's appropriately named).

deb [ftp://ftp.planetmirror.com/pub/ubuntu-backports/]("ftp://ftp.planetmirror.com/pub/ubuntu-backports/") breezy-extras

Or did you want Hoary?

deb [ftp://ftp.planetmirror.com/pub/ubuntu-backports/]("ftp://ftp.planetmirror.com/pub/ubuntu-backports/") hoary-extras

I don't think there is anything in Breezy yet.

---

