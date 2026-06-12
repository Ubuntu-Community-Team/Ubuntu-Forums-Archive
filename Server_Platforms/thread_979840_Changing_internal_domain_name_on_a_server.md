---
title: "Changing internal domain name on a server"
date: 2008-11-12
forum: Server Platforms
---

### Post by rozilla on 2008-11-12
On our firewall server, we have things like DHCP, LDAP and such. The internal domain name is **asut.org**
I need to change that to **asut.net**, now. So, far I've located the following files where I need to make the changes. 

In LDAP:
```
0 dc=asut,o=nmi-net
dc: asut
objectClass: dNSDomain
objectClass: domainRelatedObject
associatedDomain: **asut.org**

```

in /etc/hostname:
```
firewall.asut.org
```

in /etc/hosts: all the hostnames containing asut.org

in /etc/hosts.allow: anything containing asut.org

in /etc/mailname: asut.org

in /etc/resolv.conf:
```
nameserver 10.0.30.1
search asut.org

```

Am I missing anything else?

---

