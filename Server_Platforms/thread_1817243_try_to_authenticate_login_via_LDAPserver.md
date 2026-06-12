---
title: "try to authenticate login via LDAPserver"
date: 2011-08-03
forum: Server Platforms
---

### Post by associates on 2011-08-03
Hi,

I was wondering if I can get some help with my query regarding login to roundcube via dovecot ldap.

I have installed and set up the openldap on Ubuntu Server 11.04 with the help of the following article

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

. I have also installed Postfix, Dovecot, Dovecot-ldap and roundcube as the mail client. Then, I went on to test if I can login through roundcube. I received "login failed". 

I'm sure the dovecot is running fine as well as Postfix and openLDAP server. All I can find from the log was "auth(default) LDAP: Can't connect to server: localhost".

I wonder if there is a way of finding out what went wrong.

Any help would be greatly appreciated.

Thank you

---

### Post by rudelgurke on 2011-08-03
Can you login to your running Dovecot directly ? If that fails too, there's something wrong with the LDAP authentication layer, maybe wrong host or IP given or something else.

---

