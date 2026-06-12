---
title: "Missing samba groups in ubuntu client authenticating ldap server"
date: 2013-03-04
forum: Server Platforms
---

### Post by damaso.hc on 2013-03-04
I have a Ubuntu 12.04 server with samba/ldap working correctly.
My ubuntu clients authenticate using nslcd and I use pam_mount to connect samba shares.
The problem is that randomly (but frequently) when I log in with ldap credentials in ubuntu 12.04 client, when I write id -a not all the groups are listed.
If I try to debug nslcd (using -d) and trying different users, with su user1, su user2, etc it always works correctly and retrieves all groups.
This problem occurs only when logging with lightdm. If I log with ssh all groups are allways there.
Sometimes I log in with lightdm and all groups are there also.
Any idea about how to proceed?
Thanks

---

