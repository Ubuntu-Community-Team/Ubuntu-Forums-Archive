---
title: "PHPLDAPAdmin and OpenLDAP"
date: 2007-11-30
forum: Server Platforms
---

### Post by rickyjones on 2007-11-30
I'm having problems using PHPLDAPAdmin with OpenLDAP.

I'm trying to setup LDAP for use with Samba for a domain project (to see how feasible it is). I followed the instructions from [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer) to install and setup the initial OpenLDAP database.

The only thing I changed was the domain (dn=example,dn=local) and the passwords assigned.

I then installed PHPLdapAdmin and when I try to login using either the admin account or the user account that the OpenLDAP Wiki page used I get the following error:

> Could not bind to the LDAP server.

LDAP said: Undefined attribute type
Error number: 0x11 (LDAP_UNDEFINED_TYPE)
Description: The attribute type specified is invalid. 

Anyone have any idea what needs to be fixed? I can connect fine anonymously but I need to login to make any changes.

Thanks!

-Richard

---

### Post by rickyjones on 2007-11-30
Solved.

In the phpLDAPadmin config.php file I changed the line:

```
$ldapservers->SetValue($i,'login','attr','dn');

```

To:
```
$ldapservers->SetValue($i,'login','attr','cn');

```

Now I can login with the Admin user.

Anyone know how to contact the writer of the wiki article ([https://help.ubuntu.com/community/InstallingphpLDAPadmin)?](https://help.ubuntu.com/community/InstallingphpLDAPadmin)?) I recommend that the author update their directions to show what I had to do. Obviously the default install, which he writes about, does not work so easily with OpenLDAP based on the original directions.

-Richard

---

### Post by albertlash on 2008-02-03
Worked for me too - thanks!

---

### Post by mohammadrizki on 2008-05-03
Works for me too, thanks a lot...

---

