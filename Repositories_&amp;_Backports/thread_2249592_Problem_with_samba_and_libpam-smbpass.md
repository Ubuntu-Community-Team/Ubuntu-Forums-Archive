---
title: "Problem with samba and libpam-smbpass"
date: 2014-10-23
forum: Repositories &amp; Backports
---

### Post by sds2 on 2014-10-23
[SIZE=2][FONT=arial]Hello,

After an upgrade from 12.04 to 14.04, the well-know problem "no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory" has appears.

With google i have find two solutions :

-  apt-get remove libpam-smbpass

and

-[COLOR=#333333]"pam-auth-update" and remove "SMB password synchronization"


Both are not good for me because, i need to keep the password synchronization.

My question is simple, why there are no new version for the package of "libpam-smbpass" or "samba" on the ubuntu repository (new version exist!) ?

Does it will come soon ?

Is there an other solution to fix the problem, and keep the password synchronization ?


[/COLOR][/FONT][/SIZE][B][SIZE=2][FONT=arial]
[/FONT][/SIZE][/B]

---

