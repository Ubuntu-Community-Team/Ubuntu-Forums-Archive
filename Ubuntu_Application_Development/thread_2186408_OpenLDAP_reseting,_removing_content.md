---
title: "OpenLDAP reseting, removing content"
date: 2013-11-07
forum: Ubuntu Application Development
---

### Post by tuxia on 2013-11-07
I need to remove every configuration/schema/database.

Is it possible and if so how?

So far
```
sudo apt-get purge slapd ldap-utils
```

remove
```
/etc/ldap

/etc/openldap

/var/lib/ldap
```

and
```
sudo apt-get install slapd ldap-utils
```

tried to
```
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f backend2.example.com.ldif
```

still getting 80 error, which means, according to my restricted knowledge, ldap already has modules and cn s in ldif file.

---

