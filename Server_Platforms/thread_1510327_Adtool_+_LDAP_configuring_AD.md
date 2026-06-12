---
title: "Adtool + LDAP configuring AD"
date: 2010-06-15
forum: Server Platforms
---

### Post by lunix- on 2010-06-15
Adtool - "Invalid credentials" when LDAP to Active Directory

Running Lucid server edition

And trying to connect to my AD Domain Controller.  Want to be able to automate user creation and deletion from a linux server using adtool and bash (i hate vbs)

The problem is; I keep getting "Invalid Credentials" every time I try to use adtool for some action.. Cant even adtool list "ou=Users"

This is error message:

```
bind: : Invalid credentials (49)
	additional info: 80090308: LdapErr: DSID-0C090334, comment: AcceptSecurityContext error, data 525, vece
```

This is my setup:

Admin username: adminuser
Admin password: adminpassword       (yeah right :p)

/etc/adtool.cfg:
```
uri ldap://myserver.foo.com
binddn cn=adminuser,cn=Users,dc=foo,dc=com
bindpw adminpassword
searchbase dc=myserver,dc=foo,dc=com
```


/etc/ldap/ldap.conf:
```
BASE    dc=myserver,dc=foo,dc=com
URI     ldap://myserver.foo.com ldaps://myserver.foo.com
TLS_REQCERT allow
```

in adtool I do try to change between ldap and ldaps, but neither work..
and ports open on server:
636/tcp  open  ldapssl
389/tcp  open  ldap

(linux server is already a a part of the domain and can talk with AD trough winbind and kerberos,, so there is maybe a easier way than adtool+ldap to administer users?  I can list users in AD using winbind and "kinit adminuser" works without errors :)) 

Any ideas? Please help :)

---

### Post by bttw on 2010-08-03
I'm running into the same problem. Was a solution ever found?

---

### Post by emmanux on 2011-12-12
> **bttw said:**
> I'm running into the same problem. Was a solution ever found?

Someone tried this?
[http://www.beyondtrust.com/Technical-Support/Downloads/PowerBroker-Identity-Services-Open-Edition/](http://www.beyondtrust.com/Technical-Support/Downloads/PowerBroker-Identity-Services-Open-Edition/)

---

