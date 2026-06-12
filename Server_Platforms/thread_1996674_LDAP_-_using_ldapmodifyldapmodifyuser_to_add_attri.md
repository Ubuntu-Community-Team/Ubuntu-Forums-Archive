---
title: "LDAP - using ldapmodify/ldapmodifyuser to add attributes to existing entries"
date: 2012-06-04
forum: Server Platforms
---

### Post by ranger12 on 2012-06-04
Hi all, I am having trouble adding additional attributes to existing entries in my LDAP database. I have no trouble adding new entries or using ldapmodify/ldapmodiyuser to edit existing attributes in entries but I cannot seem to be able to add additional attributes to entries. The server is 12.04 Server Edition. Here is the attributes in my entries so far:

dn: 
objectClass: account
objectClass: posixAccount
uid: 
uidNumber:
gidNumber:
homeDirectory:
loginShell:
gecos:
description: 
userPassword::
cn: 

All I would like to do is add the displayName attribute, but according to the research I have done I need to add the inetOrgPerson objectClass but I cannot do that either since it reports I need the cn attribute. I wonder if anyone has dealt with this issue and can give me some pointers on adding attributes to existing entries.

---

### Post by ranger12 on 2012-06-04
Well this is odd, when I use ldapmodifyuser and make the changes as so I get:

# Enter your modifications here, end with CTRL-D.
dn: uid=travis,ou=People,dc=elrancho,dc=net
changetype: modify

add: objectClass
objectClass: person
-
add: sn
sn: Ritchie
Successfully modified user entry uid=travis,ou=People,dc=elrancho,dc=net in LDAP

However when I do ldapfinger on the entry travis, it does not show the objectClass person or the sn attribute. Apparently modifying existing attributes is a lot easier than adiding new ones. Obviously this is not the way to do it.

---

### Post by ranger12 on 2012-06-04
Okay, never mind. I found a better solution. I modified the ldapadduser.template and added the objectClasses and attributes I wanted. I then deleted the old ldap accounts and then recreated them using the modified template. The entires now have the attributes I want. I also discovered the ability in the ldapscipts.conf file to automatically create the user's home directory. All works great now.:)

---

