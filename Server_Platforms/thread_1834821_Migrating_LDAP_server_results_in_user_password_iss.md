---
title: "Migrating LDAP server results in user password issues"
date: 2011-08-28
forum: Server Platforms
---

### Post by gr33p on 2011-08-28
Hopefully someone can point me in the right direction as I appear to be going around in circles at this stage.

I  am attempting to migrate from one server running OpenLDAP 2.4.9  configured with old style slapd.conf to a new server running openldap  2.4.23 with the dynamic cn=config setup on Ubuntu 11.04.
 
I've successfully exported / imported via slapcat and slapadd and  using phpLDAPadmin I can browse all my users.  The issue I run into is  the use passwords do not work when I try to log into services (e.g.  IMAP).   
 
Using phpLDAPadmin I perform a password compare and it returns a mismatch.  

Looking  at the slapcat output for a user, the "userPassword" is afaik md5 run  though base64 and presented as such but once bas64 is decoded it matches  what phpLDAPadmin reports if I export the user.
 
```
userPassword:: e01somedandomdataPT0= 
```

I docode this :
```
     
user@server.tld$ perl <<EOF
> use MIME::Base64;
> print decode_base64('e01somedandomdataPT0=') . "\n";
> EOF
{MD5}thisisahash==

```Exporting the user in  phpLDAPadmin and compare it's reported *userPassword* to the above perl  output and they match.  As they match I am at a loss as to why the  password is not accepted when I try to login via IMAP or check password  in phpLDAPadmin.   As soon as I change the password, the account works  find and the user can log in.
 
Any help greatly appreciated, as I would rather not have to reset user passwords!

---

