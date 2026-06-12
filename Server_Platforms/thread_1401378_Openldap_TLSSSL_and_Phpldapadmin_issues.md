---
title: "Openldap TLS/SSL and Phpldapadmin issues"
date: 2010-02-08
forum: Server Platforms
---

### Post by nyu2007 on 2010-02-08
Hi,

I have an issues with phpldapadmin
After setup Openldap server with TLS/SSL use ldaps, I install phpldapadmin and have an issue

LDAP Server is configured and running.
I make some ldapsearch and it oki.

I couldn't use https to browse LDAP server when I use http and I can't connect **Could not start TLS. Please check your LDAP server configuration.**

This is my config

```
/etc/ldap/ldap.conf
BASE    dc=microhelpdesk,dc=net
HOST    ldap-svr.microhelpdesk.net
URI     ldaps://ldap-svr.microhelpdesk.net
TLS_CACERT /var/myssl/cacert.pem
TLS_CACERTDIR /var/myssl/
TLS_REQCERT     allow
```

```
/usr/share/phpldapadmin/config/config.php
$ldapservers->SetValue($i,'server','name','MicroHelpdesk LDAP Server');
$ldapservers->SetValue($i,'server','host','ldaps://192.168.0.5:636');
$ldapservers->SetValue($i,'server','base',array('dc=microhelpdesk,dc=net'));
$ldapservers->SetValue($i,'server','auth_type','session');
$ldapservers->SetValue($i,'login','dn','cn=Admin,dc=microhelpdesk,dc=net');
$ldapservers->SetValue($i,'login','pass','');
$ldapservers->SetValue($i,'server','tls',true);

```
Help me.

Thanks and best regards,
NyU

---

### Post by nyu2007 on 2010-02-10
No one help me, pls.

---

### Post by blink0 on 2010-04-07
Hey nyu2007,

I also have the same setup (OpenLDAP 2.4.19 on a Ubuntu Hardy and phpLDAPadmin 1.1.0.4 on a Ubuntu Hardy) and I seem to have random failures when using SSL (ldaps:// without TLS on port 636) or TLS (ldap:// with TLS on port 389). It works half the time, the other half it says the username is wrong or that the TLS connection couldn't be established. PHPldapadmin's logs don't give any errors, and the slapd's logs just say "conn=1735 fd=17 closed (TLS negotiation failure)". Of course the loglevel could be increased...

Anyway, I'm guessing this is the wrong location to be complaining about this, maybe we should take it up to phpldapadmin's forums?

Cheers

---

