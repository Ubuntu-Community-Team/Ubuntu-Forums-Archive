---
title: "Samba LDAP. User groups: 'None'"
date: 2012-07-04
forum: Server Platforms
---

### Post by PycT on 2012-07-04
Hi
I would like to run logon scripts (on Windows workstations) based on nested group membership. I tried a lot of utilities like KIXTART, IFMEMBER, MEMBEROF and finaly found [simple vbs displaying user's groups]("http://www.winfrastructure.net/article.aspx?BlogEntry=Get-users-groups-using-VBScript")
Result always the same: user is in the group MYDOMAIN\None. :(
I can see all domain users and groups, when changing user's file access permissions.

Can anyone help?

My server:
Ubuntu 12.04
SambaLdap 3.5.11
Gosa 2.7.4 (posixgroup)

---

