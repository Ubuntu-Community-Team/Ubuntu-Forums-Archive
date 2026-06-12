---
title: "LDAP issues"
date: 2007-03-17
forum: Server Platforms
---

### Post by cyris| on 2007-03-17
Hey everyone.

My co-worker and I are about to setup an LDAP server for storing qmail, posix, and samba accounts.

We understand we have to have the appropriate schema's in slapd.conf so we have all the object classes we need :D

But we are kinda puzzled on how to create an ldap directory structure that will house all our accounts and make qmail, samba and posix accounts all happy.

For example, Please consider this ldap directory structure (I know I may not have the correct objectClass's loaded, but for this example its fine)

dn: dc=company,dc=local
objectClass: top
objectClass: dcObject
objectClass: organizationalUnit
dc: company
ou: Bigal LDAP server

dn: ou=management,dc=company,dc=local
objectClass: top
objectClass: organizationalUnit
ou: management
description: Management Staff Accountsr

dn: ou=standard,dc=company,dc=local
objectClass: top
objectClass: organizationalUnit
ou: management
description: Standard Staff Accounts

Now, every ldap howto i've seen has me make a ldap directory structure suited for the guide, which makes sense, but how would i go about creating a directory structure for lets say posix accounts and email accounts.

So basiclly what im asking is how does posix accounts, or samba accounts know how to find the data they need in MY custom ldap directory structure ? How will samba know to look in "ou=Management,dc=iainc,dc=local" ?

I hope people understand my question :D

Thanks all!

---

