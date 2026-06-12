---
title: "[LDAP] ldapscripts not using given templates"
date: 2011-05-29
forum: Server Platforms
---

### Post by Johnco on 2011-05-29
I have configured and installed LDAP.

in /etc/ldapscripts/ldapscripts.conf I have set:

UTEMPLATE="/etc/ldapscripts/ldapadduser.template"

File which contains:

dn: uid=<user>,<usuffix>,<suffix>
objectClass: account
objectClass: posixAccount
cn: <ask>
sn: <ask>
givenName: <ask>
displayName: <ask>
uid: <user>
uidNumber: <uid>
gidNumber: <gid>
homeDirectory: <home>
loginShell: <shell>
gecos: <ask>
mail: <ask>
initials: <ask>

However, when I run ldapadduser the user is created but none of these values are asked and just sets the default to everything (for instance gecos is set to <user>, along as cn, and sn is not even set)


Any ideas?

---

### Post by Johnco on 2011-05-29
Figured it out myself... turns out the UTEMPLATE var was being redefined later on the same script.

Thanks anyway!

---

