---
title: "ldap samba/unix password authentication management"
date: 2010-02-10
forum: Server Platforms
---

### Post by Pseudonomous on 2010-02-10
Hi everybody,

I maintain a samba PDC for a small business, our current setup does not work very well; on a hardware upgrade I directled imported the old ldap database and attempting to add machines to the domain causes all sorts of trouble.

I'm 95% sure the original database (which predates my employment) was created using the idealx smb-ldap tools, unfortunately on our current platform (debian lenny) these tools seem to be broken; the only things
they seem to do reliably are set passwords and add posix users, asking them to do anything involving samba/windows causes errors.  The idealx tools seem to be abandoned, and I don't know enough perl to try and fix them.

Since the idealx scripts seem to be abandoned, and most of the good samba+ldap how-tos references the idealx tools, I was wondering what people use nowadays to manage there ldap directories; surely they aren't importing .ldif files to add new users/machines like I've been doing.  Are people just writing thier own management scripts/web-apps?  Or are the smb=ldap tools just broke on debian?

I could write my own, but I have trouble figuring out how to generate the NT/LM password hashes and proper SIDs, does anybody have anything they could point me to about this?

---

### Post by joberly on 2010-02-10
Something like [http://phpldapadmin.sourceforge.net](http://phpldapadmin.sourceforge.net) ? Seems current, latest release is January of this year!

Also, [http://www.ldap-account-manager.org/](http://www.ldap-account-manager.org/).

I haven't used either, but hopefully they can help you!

---

