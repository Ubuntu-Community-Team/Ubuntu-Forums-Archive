---
title: "update ubuntu sevrer"
date: 2006-03-08
forum: Server Platforms
---

### Post by davebradford on 2006-03-08
when dapper is released next month how easy is it to update from 5.10? i am running a server at the moment with a fair few things setup, and would rather not restart but then again this might be nessessary :o( is there a way to update to dapper via apt-get without losing anything? 

p.s whats the release date of dapper?

thx

---

### Post by 4dz0 on 2006-03-08
For the update take a look at this:

[http://www.macewan.org/2006/02/23/upgrading-breezy-to-dapper/](http://www.macewan.org/2006/02/23/upgrading-breezy-to-dapper/)

The expected release date for dapper is the 20th April

---

### Post by az on 2006-03-08
[QUOTE=davebradford]when dapper is released next month how easy is it to update from 5.10? i am running a server at the moment with a fair few things setup, and would rather not restart but then again this might be nessessary :o( is there a way to update to dapper via apt-get without losing anything? 

p.s whats the release date of dapper?

thx[/QUOTE]
sudo apt-get dist-upgrade after changing your sources.list to point to dapper.

It should release around the 20th.

---

### Post by davebradford on 2006-03-08
does this mean i will not have to restart my server?

---

### Post by bikeboy on 2006-03-08
It will most likely do a kernel update (unless you can prevent that without causing problems) and these require a restart.

---

### Post by Klaidas on 2006-03-08
> It should release around the 20th.
Almost my birthday :) A cool present! \\:D/

---

### Post by nocturn on 2006-03-08
[QUOTE=Klaidas]Almost my birthday :) A cool present! \\:D/[/QUOTE]

Mine too.  If they are a couple of days late ;-)

---

### Post by az on 2006-03-08
[QUOTE=davebradford]does this mean i will not have to restart my server?[/QUOTE]
No.  You will be able to keep running the old kernel.  You can either pin the kernel version so that you do not get a new version installed, or do the dist upgrade and you will have the new kernel installed, but you are not *required* to boot into it right away.

The next time you will boot, you will boot the new kernel by default.  You can also set grub to boot the old kernel by default, if you want.

You can also dist-upgrade and remove the new kernel if you prefer to continue using the older kernel.

The options are endless!

---

