---
title: "ldap authtication with minimal uid"
date: 2008-08-12
forum: Server Platforms
---

### Post by darthkhamul on 2008-08-12
Hello
I've a server authenticated by ldap, but we share the ldap server with another departement in our business. Our users have uid between 2000 and 2999 so i would like to autheticate only users in this range.
I've set the pam_uid_min and pam_uid_max in /etc/ldap.conf but it does nothing at all. 
If someone has an idea to solve this problem....
Thanks

ps: the config is the default one created by auth-client-config utility.

---

