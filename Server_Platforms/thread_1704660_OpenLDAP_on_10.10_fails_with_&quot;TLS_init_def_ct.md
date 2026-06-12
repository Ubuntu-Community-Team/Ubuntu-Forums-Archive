---
title: "OpenLDAP on 10.10 fails with &quot;TLS init def ctx failed: -1&quot;"
date: 2011-03-11
forum: Server Platforms
---

### Post by ozmaXTor on 2011-03-11
Guys,

So I've read about the Debian/Ubuntu distros migrated to gnutls implementation for TLS/SSL. Fine with me, but I've spent the last week trying to configure OpanLDAP with TLS/SSL without success, keep getting stuck at "TLS init def ctx failed: -1" error. I'm guessing it may be caused by the certificate, but I followed the instructions at

[https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html)

on my own laptop it works like a charm, just not on the server for whatever reason....

OK there's a bit more detail:

Server: Ubuntu 10.10 32bit
OpenLDAP: 2.4.23-0ubuntu3.4 (installed via apt-get)
Gnutls: 2.8.6-1 (comes with the OS)

I'm still using /etc/ldap/slapd.conf to configure OpenLDAP (I know it's no good but I've got this config file from the existing working server so thought I just take advantage of it). This config works on my laptop. Some details:

```
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
access to attrs=userPassword
    by dn="cn=admin,dc=organisation,dc=com" write
    by anonymous auth
    by self write
    by * none
.
.
.
TLSCACertificateFile /etc/ssl/certs/cacert.pem
TLSCertificateFile /etc/ssl/certs/server_slapd_cert.pem
TLSCertificateKeyFile /etc/ssl/private/server_slapd_key.pem
```

I've added the openldap user to the root group so that it can read the private keys:

```
root@server:/etc/ssl/private# ls -l 
total 8
-rw-r--r-- 1 root root 1675 2011-03-11 15:53 cakey.pem
-rw-r--r-- 1 root root 1675 2011-03-11 15:55 server_slapd_key.pem

```
I follow the instructions step-by-step exactly like the guide mentioned above however I still get the "TLS init def ctx failed: -1" error.

This is driving me nuts and basically I'm running out of hair to pull. could someone shed some lights please, thanks in advance.

TW

---

### Post by ozmaXTor on 2011-03-13
OK I managed to solve this one - it was caused by directory permission on /var/lib/ldap. I created group ssl-cert, added user openldap into the group, then "chgrp -R ssl-cert /var/lib/ldap/*", then "chmod -R g+rw /var/lib/ldap/*", and things started to work for me!

---

