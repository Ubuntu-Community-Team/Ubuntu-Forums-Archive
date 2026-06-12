---
title: "LDAP: Disabling anonymous access also prevents services to authenticate"
date: 2014-10-04
forum: Server Platforms
---

### Post by richard51 on 2014-10-04
I wanted to tighten security on my **ldap** servers, and disable anonymous access. Authentication is provided by **kerberos** for both users and services, which in turn are mapped to **ldap** accounts. I created the following **ldif** file to disable anonymous access, but I can no longer log-in from client machines.
```

dn: cn=config
changetype: modify
add: olcDisallows
olcDisallows: bind_anon

dn: cn=config
changetype: modify
add: olcRequires
olcRequires: authc

dn: olcDatabase={-1}frontend,cn=config
changetype: modify
add: olcRequires
olcRequires: authc

```

System log indicates that some services (*which are mapped*), cannot authenticate unless I allow anonymous access. Is there a work-around for this?

---

### Post by richard51 on 2014-10-05
The problem was my fault, I hadn't added the host to the keytab on some of the client machines. **BUT**, I have now created another problem... **sudo-ldap** causes a **seg fault** when you set **USE_SASL** **on**. It does have the path to the Kerberos 5 credential cache, and the right credentials (*loaded at boot by k5start*). Any ideas?

---

