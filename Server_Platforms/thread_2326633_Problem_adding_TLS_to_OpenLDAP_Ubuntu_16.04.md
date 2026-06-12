---
title: "Problem adding TLS to OpenLDAP Ubuntu 16.04"
date: 2016-06-02
forum: Server Platforms
---

### Post by grandcross on 2016-06-02
Setting up an OpenLDAP server. I notice the documentation isn't up to date for version 16. For example, the docs refer to the hdb backend instead of the mdb, dc=example,dc=com isn't automatically created, etc...

When I get to the section on adding TLS [https://help.ubuntu.com/lts/serverguide/openldap-server.html#openldap-tls]("https://help.ubuntu.com/lts/serverguide/openldap-server.html#openldap-tls"), all goes well until I try to add the certificate files to LDAP. I create the certinfo.ldif file as described, but when I run it I get this:

```
root@ldap:~# ldapmodify -Y EXTERNAL -H ldapi:/// -f certinfo.ldif 
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
modifying entry "cn=config"
ldap_modify: Other (e.g., implementation specific) error (80)
```


Here is my certinfo.ldif:

```
dn: cn=config
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem
-
add: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ssl/certs/ldap_slapd_cert.pem
-
add: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ssl/private/ldap_slapd_key.pem
```

I have no clue what's wrong or where to look. Suggestions?

---

### Post by grandcross on 2016-06-03
Follow up to my earlier post. I broke this down into steps, adding each element one at a time. Here is my ldif:

[FONT=Fixedsys]dn: cn=config
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem[/FONT]

This is the result when I run ldapmodify:

[FONT=Fixedsys]root@ldap-test:~# ldapmodify -Y EXTERNAL -H ldapi:/// -f certinfo1.ldif 
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
modifying entry "cn=config"
ldap_modify: Inappropriate matching (18)
	additional info: modify/add: olcTLSCACertificateFile: no equality matching rule[/FONT]

I have no idea what this means. Yes, I'm new to LDAP.

---

### Post by grandcross on 2016-06-03
Well, I found my own solution. It can be found here:

[http://serverfault.com/questions/455529/openldap-tls-authentication-setup]("http://serverfault.com/questions/455529/openldap-tls-authentication-setup")

---

