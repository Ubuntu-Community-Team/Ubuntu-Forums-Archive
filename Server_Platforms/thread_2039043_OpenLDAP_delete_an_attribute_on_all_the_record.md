---
title: "OpenLDAP delete an attribute on all the record"
date: 2012-08-07
forum: Server Platforms
---

### Post by salton on 2012-08-07
Hello

I need to delete an attribute on each record on the entire database. I am using the following method that works for single entire but when I remove uid=usertest,ou=People then it doesn't work. I get an error that "telephonenumber" attribute not found

ldapmodify -v -h localhost -x  -D "cn=admin,dc=test,dc=com" -w pass123 -f ./input.ldif


input.ldif:

dn:uid=usertest,ou=People,dc=test,dc=com
changetype: modify
delete: telephoneNumber



#>ldapmodify -v -h localhost -x  -D "cn=admin,dc=test,dc=com" -w pass123 -f ./input.ldif
ldap_initialize( ldap://localhost )
delete telephoneNumber:
modifying entry "dc=sag,dc=com"
modify complete
ldapmodify: No such attribute (16)
        additional info: modify/delete: telephoneNumber: no such attribute

---

