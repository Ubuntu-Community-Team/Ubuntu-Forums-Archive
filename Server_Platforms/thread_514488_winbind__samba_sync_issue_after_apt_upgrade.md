---
title: "winbind / samba sync issue after apt upgrade"
date: 2007-07-31
forum: Server Platforms
---

### Post by merkur2k on 2007-07-31
After a recent upgrade of my webapp developement box here at work, the winbind database has somehow gotten out of sync with our domain controller.
if I do a 'wbinfo -r user1' it will show the user belonging to groups they they are not a member of.
however if I do a 'getent group group1' it correctly shows that user1 is a member of group1.
any ideas what could be going on here, or how to resync things?
This is Dapper Server 6.06
Samba 3.0.22
Winbind 3.0.22
connected as a member of a NT4 domain.
I need to resolve this as it is currently preventing me from applying updates to the production server.

---

### Post by thegibbling on 2008-03-13
Hi there,
I believe we are in similar boats.  The group info on my NAS = unixraid:x:10007 and the group info on my webserver = unixraid:x:10008.  I would also be curious if anyone has any ideas on this issue.

---

