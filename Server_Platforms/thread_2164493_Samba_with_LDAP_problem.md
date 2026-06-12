---
title: "Samba with LDAP problem"
date: 2013-07-31
forum: Server Platforms
---

### Post by anondude on 2013-07-31
I've followed the server guide to set up Samba with LDAP backend:

[https://help.ubuntu.com/12.04/serverguide/samba-ldap.html](https://help.ubuntu.com/12.04/serverguide/samba-ldap.html)

After I finished configuring everything following the instructions above, I started getting a 1 minute+ delay every time I try to log in to the  server,  regardless of what user I log on as, followed by this error:

> Failed to add entry for user (user name).

The same delay happens every time I'm asked to enter my password for a  sudo command. I'm guessing there's a timeout of some sort occurring  here, but I'd like someone more knowledgeable to help me out.

If you need more info, ask me and I'll try to provide as much as I can.
I'm running Ubuntu Server 12.04LTS.

Thanks

---

### Post by anondude on 2013-08-04
Bump.
Anyone?

---

### Post by anondude on 2013-08-07
2nd Bump with update...
Still haven't been able to figure this problem out. It seems to be a connection problem between samba and LDAP, but I haven't been able to figure out why or what is causing it.

---

