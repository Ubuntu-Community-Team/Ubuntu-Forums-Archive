---
title: "objectClass in openldap."
date: 2012-12-08
forum: Server Platforms
---

### Post by honey_bee on 2012-12-08
I am working on openldap in my ubuntu box  as testing.I create a base file to discuss with you about objectClass functionality & its impact if we not write.I write objectClass two times i.e top and domain .What does it mean ? The 2nd one is drived from the firect objectClass like parents child relation ?
# vim base.ldif base.ldif dn: dc=test,dc=local dc: test objectClass: top objectClass: domain Now I create add two OUs and does not add objectClass:top in both sales and marketing.
To add two OUs i.e Sales and Marketing 
**dn: ou=Sales,dc=test,dc=local ou: Sales objectClass:organizationalUnit dn: ou=Marketing,dc=test,dc=local ou: Marketing objectClass: organizationalUnit**  
The confusion is should use all the parent objectClass and chield objectClass ? If we not add what impact will be on the structure ? In the following I use objectClass top and organizationalunit
**dn: ou=Sales,dc=test,dc=local ou: Sales objectClass: top objectClass:organizationalUnit dn: ou=Marketing,dc=test,dc=local ou: Marketing objectClass: top objectClass: organizationalUnit** Please guide me which one is correct ? thanks 
honey.

---

