---
title: "DHCP okay to disable for dialup only?"
date: 2006-01-10
forum: Server Platforms
---

### Post by preptheshipfortakeoff on 2006-01-10
i use dialup only to connect to the internet with Ubuntu Breezy. i removed all the DHCP packages because i guessed they were not useful for me i do not have a home network only one computer and i connect to the internet with dialup. when i removed it it said that it was removing ubuntu-minimal but i removed ubuntu-desktop too and some other and no ill effects.

should this be fine?

one more question if you please, how do i close this as i not need it:

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -

---

### Post by LordHunter317 on 2006-01-10
It's fine.

That's the CUPS printer system, you could stop it with:```
/etc/init.d/cupsys stop
``` for one boot.  If you have a printer though, you need that running.  It's listening locally and not a security issue of any sort.

---

### Post by az on 2006-01-10
[QUOTE=preptheshipfortakeoff]i removed it it said that it was removing ubuntu-minimal but i removed ubuntu-desktop too and some other and no ill effects.

     -[/QUOTE]
Ubuntu-desktop is a meta-package.  It's only pourpose in life is to depend on other packages.  If one package is replaced by another package from one release to the next (for example, xpdf was the pdf reader inHoary, but evince is the pdf reader in breezy) a meta package will take care of that.  

The metapackage that is resonsable for supplying the pdf reader stays the same, but the package it depends on gets changed. 

Otherwise, if you dist-upgraded from one release to another, you would not be guaranteed a complete system.

So, you can remove that now, but if you ever want to upgrade to the next release of ubuntu (Dapper, in april) do the upgrade and then check to see what installing the ubuntu-desktop package would install and decide whether you need those packages or not.

---

