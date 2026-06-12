---
title: "Samba + Cups + Windows client drivers problem"
date: 2007-02-10
forum: Server Platforms
---

### Post by localzuk on 2007-02-10
I have set up a dapper box with samba + winbind and successfully joined it to our Active directory. I have also set up cups and enabled web configuration - and this all works.

In my smb.conf file I have set up pretty much the basic print set up, per chapters 21 and 22 of the samba book at samba.org. I have a [printers] section set up exactly as described in the basic cups section, except for the printer admin line which I have put in administrator and @adm (administrator is my default user). I have then set up [print$] per the instructions in chapter 21, again using my own groups.

I have then used net groupmap modify ntgroup="Domain Admins" unixgroup=adm etc... to map the various groups to my own groups.

When I then try to load the drivers for a printer using the Windows GUI method the Add Driver button is greyed out.

Is this something I have done wrong? Or something I've missed?

---

### Post by localzuk on 2007-02-12
Bump...

---

