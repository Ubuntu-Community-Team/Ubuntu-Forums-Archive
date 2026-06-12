---
title: "Authenticate with multiple LDAP servers"
date: 2010-11-17
forum: Server Platforms
---

### Post by hewbert on 2010-11-17
Greetings,

I'm hoping to authenticate a server with 2 different LDAP servers, if possible.  They are completely separate domains (not a failover or anything).  Firstly, is what I'm looking for possible?  This is a 10.04 machine.  Additionally, one server requires authentication while the other doesn't.  Here's an illustration of what I'm talking about (this is what /etc/nslcd.conf might look like for each one):

```

uri ldaps://host1.domainone.net/
base dc=host1,dc=domainone,dc=net
binddn cn=auth,ou=People,dc=domainone,dc=net
bindpw xxxxxx


uri ldaps://host2.org.orglocal/
base dc=host2,dc=org,dc=orglocal
binddn dc=org,dc=orglocal

```

---

### Post by druhboruch on 2010-11-17
If your user changes password how would you propagate the change to the other LDAP server?

To make it work I think that your servers must be in sync.

You should look at sssd instead. (if I correctly understand what you are trying to achieve.

---

### Post by hewbert on 2010-11-17
> **druhboruch said:**
> If your user changes password how would you propagate the change to the other LDAP server?

To make it work I think that your servers must be in sync.

You should look at sssd instead. (if I correctly understand what you are trying to achieve.


Each server has a different set of users.  What I'm trying to accomplish is similar to how Mac OS X does it.  You can join many different authentication servers/domains and set your search paths as appropriate.  It'd look at each server until it found a match.

---

### Post by druhboruch on 2010-11-17
It is a very interesting question.
SSSD supports multiple domains:
It may just do what you need:
[http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/sect-SSSD_User_Guide-Introduction-SSSD_Features.html](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/sect-SSSD_User_Guide-Introduction-SSSD_Features.html)

---

