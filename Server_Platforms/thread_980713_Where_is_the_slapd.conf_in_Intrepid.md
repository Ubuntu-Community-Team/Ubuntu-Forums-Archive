---
title: "Where is the slapd.conf in Intrepid?"
date: 2008-11-13
forum: Server Platforms
---

### Post by Jan-42 on 2008-11-13
Hi,

I tried to install ldap, following the instructions on [https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix](https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix) . But there is no /etc/ldap/slapd.conf in 8.10?!

---

### Post by kaptengu on 2008-11-13
Have you tried:
```
locate slapd.conf
```

---

### Post by Jan-42 on 2008-11-13
Yes, there is none.
```
jan@Erwin:~$ locate slapd.conf
/usr/share/man/man5/slapd.conf.5.gz
/var/lib/dpkg/info/slapd.conffiles
/var/lib/dpkg/info/slapd.config

```

---

### Post by M1Sports20 on 2008-11-15
8.10 uses the new openldap configuration([http://www.ubuntu.com/getubuntu/releasenotes/810overview#OpenLDAP%20using%20%27%27cn=config%27%27](http://www.ubuntu.com/getubuntu/releasenotes/810overview#OpenLDAP%20using%20%27%27cn=config%27%27))

openldap is moving to storing its configuration in and ldap backend.  It will no longer use the single file slapd.conf.

Right now I have not been able to find much documentation on this new configuration.  If you want you can still use the old method.  You just have to create a slapd.conf file.  Then change the file /etc/default/slapd.  Point the var: SLAPD_CONF to your slapd.conf

---

### Post by zeuscanthearu on 2008-11-19
You could have a look [here]("http://www.openldap.org/doc/admin24/slapdconf2.html")

---

