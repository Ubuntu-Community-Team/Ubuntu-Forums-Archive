---
title: "Courier-ldap schema?"
date: 2007-07-12
forum: Server Platforms
---

### Post by Koybe on 2007-07-12
Hello,

I try to put all this in place, I had to do it on debian before. I need to install the courier schema to my slapd server. But I can't find it on my server, all apckages installed.

```
jh@ubufa:/usr/share/doc/courier-ldap$ sudo find / -name *schema
/etc/ldap/schema
/etc/ldap/schema/inetorgperson.schema
/etc/ldap/schema/core.schema
/etc/ldap/schema/misc.schema
/etc/ldap/schema/mozillaabpersonalpha.schema
/etc/ldap/schema/evolutionperson.schema
/etc/ldap/schema/dyngroup.schema
/etc/ldap/schema/ppolicy.schema
/etc/ldap/schema/java.schema
/etc/ldap/schema/corba.schema
/etc/ldap/schema/openldap.schema
/etc/ldap/schema/cosine.schema
/etc/ldap/schema/rfc2307bis.schema
/etc/ldap/schema/nis.schema
/var/www/egroupware/phpgwapi/doc/ldap/rfc2307bis.schema
/var/www/egroupware/addressbook/doc/mozillaabpersonalpha.schema
/var/www/egroupware/addressbook/doc/evolutionperson.schema
/var/www/egroupware/addressbook/doc/mozillaorgperson.schema
/var/www/egroupware/emailadmin/doc/qmailuser.schema
/var/www/egroupware/emailadmin/doc/dbmail.schema

```Does anyone know where I can get it? Or what do I have to do to make courier working with ldap?

---

### Post by Koybe on 2007-07-12
I can't find it in any package. But i took it in the source file @ [http://www.courier-mta.org/](http://www.courier-mta.org/)

---

