---
title: "Move OpenLDAP users to OU"
date: 2017-09-19
forum: Server Platforms
---

### Post by e.ms on 2017-09-19
Hello everybody,

I actually thought that there is a simple way to move a user from one OU to another. Does anyone have a command for an .ldif file to move a user to another OU.

I have the following in my test.ldif file entered:
```
dn: cn=Vorname Nachname,ou=Users,dc=local,dc=net
changetype: modify
replace: ou
ou: newOU
```

I am doing the following:
**ldapmodify -x -c -D cn=admin,dc=local,dc=net -W -f test.ldif**

The user only receives a new attribute (ou: newOU). However, the OU was not changed.

---

### Post by ajgreeny on 2017-09-19
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

### Post by darkod on 2017-09-19
I haven't worked with OpenLDAP but according to these instructions [https://www.digitalocean.com/community/tutorials/how-to-use-ldif-files-to-make-changes-to-an-openldap-system](https://www.digitalocean.com/community/tutorials/how-to-use-ldif-files-to-make-changes-to-an-openldap-system) moving users to another OU is done with a different command (modrdn). Scroll almost all the way to the bottom to find the section "Moving an Entry".

---

### Post by e.ms on 2017-09-22
Hello darkod and many thanks!

Here is the correct syntax:
```
dn: cn=Vorname Nachname,ou=Users,dc=local,dc=net
changetype: modrdn
newrdn: cn=Vorname Nachname
deleteoldrdn: 0
newsuperior: ou=UsersNEW,dc=local,dc=net
```

---

