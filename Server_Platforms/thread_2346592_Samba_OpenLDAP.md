---
title: "Samba OpenLDAP"
date: 2016-12-16
forum: Server Platforms
---

### Post by asadraza5 on 2016-12-16
Hi folks.

Im trying to install SAMBA and OpenLDAP on Ubuntu Kylin 16.10 using the following guide

[https://www.unixmen.com/setup-samba-domain-controller-with-openldap-backend-in-ubuntu-13-04/](https://www.unixmen.com/setup-samba-domain-controller-with-openldap-backend-in-ubuntu-13-04/)


I get the error at the following command.
**sk@server:~$ sudo ldapmodify -Q -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/samba_indices.ldif**
The error is:
[COLOR=#333333][FONT=monospace]ldap_modify: No such object (32)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]            matched DN: cn=config[/FONT][/COLOR]


I changed the following line in samba_indices.ldif

from:
**dn: olcDatabase={1}hdb,cn=config**to:

dn: olcDatabase={1}mdb,cn=config


The error is:
[COLOR=#333333][FONT=monospace]modifying entry "olcDatabase=[/FONT][/COLOR][COLOR=#333333][FONT=monospace]{1}mdb,[/FONT][/COLOR][COLOR=#333333][FONT=monospace]cn=config"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]    ldap_modify: Other (e.g., implementation specific) error (80)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        additional info: duplicate index definition for attr "uidNumber"

Please help.

Thanks.


[/FONT][/COLOR]

---

### Post by slickymaster on 2016-12-16
*Thread moved to **Server Platforms*** which is probably a better venue for it.

---

### Post by Graham_Willis on 2016-12-17
Use a guide which is up-to-date, e.g.:

[https://help.ubuntu.com/lts/serverguide/samba-ldap.html](https://help.ubuntu.com/lts/serverguide/samba-ldap.html)

Come back here for further assistance if something goes wrong.

---

