---
title: "objectClass in openldap."
date: 2012-12-07
forum: Server Platforms
---

### Post by honey_bee on 2012-12-07
hi, 
I need guidance related to ldap LDIF file .Normally when we create a  base ldif file and rest of its contents we use word objectCalss two  times. 
Kindly just let me know that what the 1st onjectClass represent and what the 2nd represents ? 

Following is the example. 

Example-1 

dn: dc=example,dc=com,dc=au 
dc: example, 
[COLOR=Red][B]objectClass: dcObject 
objectClass: organization [/B][/COLOR]
o: example 


Example-2 

dn: ou=People, o=Ever 
ou: People 
[COLOR=Red][B]objectClass: top 
objectClass: organizationalUnit [/B][/COLOR]

Here again two times objectClass ? please just guide me. 

thanks,
honey.

---

