---
title: "Open LDAP certs &amp; TLS ubu 8.10"
date: 2009-03-26
forum: Server Platforms
---

### Post by sangamc on 2009-03-26
Hi all, 

ive been following the two sets of documentation linked below to install oLDAP on a test 8.10 server. i completed the part for creating self signed cert to use with open ldap but run into some issues when i reference the following the config

/etc/ssl/certs/cacert.pem
/etc/ssl/certs/server.crt
/etc/ssl/private/server.key

when i restart the slapd service i get an error message that doesnt reference any errors, and the service fails to start properly. what could i be doing wrong, and how can i trouble shoot.

please let me know if i need to post anymore info.

thanks



openLDAP
[https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html#openldap-configuration](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html#openldap-configuration)

certificates
[https://help.ubuntu.com/8.10/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.10/serverguide/C/certificates-and-security.html)

---

### Post by apalacheno on 2009-08-10
Hey,
try disabling AppArmor.

Cheers,
Robert

---

