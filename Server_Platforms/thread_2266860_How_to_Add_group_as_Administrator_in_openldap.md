---
title: "How to Add group as Administrator in openldap"
date: 2015-02-25
forum: Server Platforms
---

### Post by Lucas_Williams on 2015-02-25
Google and the OpenLdap Administration guide are pretty much worthless.

That being said....

I have a group in openldap, cn=Administrators,ou=Groups,dc=example,dc=com

I have a member in there called Test-Admin

I can login to LDAP with it, but cannot make any changes.

I looked up how to do this, and if there was such a file on my setup called slapd.conf, which I guess has been deprecated in version  2.4.31. 
Using ldapmodify to import this ldif fails saying it can't find the dn.

dn: cn=config
changetype: modify
access to dn.children="dc=example,dc=com"
            by self write
            by group.exact="cn=Administrators,ou=Groups,dc=example,dc=com" write
            by * auth

Running Ubuntu 14.04.2 LTS fully patched
using PHPLDAPADMIN for administration

The basic idea is that I want to add users to the Administrators group to have full access and make changes just like they are cn=admin,dc=example,dc=com.
Next, I will create a group called Help Desk, which will only be able to add and delete users from ou=Users,dc=example,dc=com, but I can't even get the first part working.

Is there any step-by-step/how-to/YouTube video/pay someone $1,000,000.00 to do this? So far, none of the above have helped. Figured I would come here. 

I know extremely little of LDAP, other than how to add objects directly to it, modify objects, update the schema, extend the schema, and generally get frustrated with this. 

Any help would be greatly appreciated.

Thanks,
Lucas Williams

---

