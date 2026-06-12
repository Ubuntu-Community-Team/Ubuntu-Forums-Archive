---
title: "Webmin LDAP User Module and phpLDAPadmin Don't Work on Karmic, Lucid"
date: 2010-05-03
forum: Server Platforms
---

### Post by guywithcable on 2010-05-03
Webmin's LDAP Users and Groups module and phpLDAPadmin stopped working after upgrading from Jaunty to Karmic.

I have been using Webmin's LDAP Users and Groups module on my company's server to administer users. It was working fine on Jaunty, but after upgrading to Karmic I get the error:

> Webmin has connected to the LDAP server, but failed to fetch the schema. Make sure that access has not been denied in the LDAP Server module.I can use the ldap tools like ldapsearch and ldapwhoami using the same credentials found in the LDAP Server module's config.

phpLDAPadmin also reports this error:

> Our attempts to find your SCHEMA have  failed (objectclasses)
**Error**:  Please contact the phpLDAPadmin developers and let them know:
[LIST]
[*]Which  LDAP server you are running, including which version
[*]What OS it  is running on
[*]Which version of PHP
[*]As well as a link to  some documentation that describes how to obtain the SCHEMA information
[/LIST]

We'll  then add support for your LDAP server in an upcoming release.I upgraded to Lucid, hoping it would fix the problem, but it did not. I still get the exact same errors.

---

### Post by guywithcable on 2010-05-03
I figured it out thanks to this post:

[http://serverfault.com/questions/81684/no-root-dse-returned-from-openldap/85917#85917](http://serverfault.com/questions/81684/no-root-dse-returned-from-openldap/85917#85917)

There is actually a bug filed for this issue:

[https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/427842](https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/427842)

The post (with instructions) reads:

> This is actually filed as bug [#427842]("https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/427842") agains Ubuntu 9.10  (karmic).
  To fix this, copy the following to fixRootDSE.ldif:
  ```
dn: olcDatabase={-1}frontend,cn=config
changetype: modify
add: olcAccess
olcAccess: to dn.base="" by * read
olcAccess: to dn.base="cn=subschema" by * read
```  And execute
  ```
sudo ldapmodify -Y EXTERNAL -H ldapi:/// -f fixRootDSE.ldif
```  This should give anonymous access to the root DSE.
 
I'm assuming this bug only affected me because I upgraded from 9.04.

---

