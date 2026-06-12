---
title: "OpenLDAP with SSL"
date: 2008-10-23
forum: Security
---

### Post by tuananh1973 on 2008-10-23
Hello,

I tried to configure openldap server with ssl on Ubuntu 8.04. I created a server certificate (self-sign), configured slapd.conf as follow.

TLSCACertificateFile server.pem
TLSCertificateFile server.pem
TLSCertificateKeyFile server.pem

I restarted slapd then tried

openssl s_client -connect localhost:636 -showcerts

it told me that

connect: Connection refused
connect:errno=29

I also tried with Centos, it just works just fine.

Please help,
Tuan Anh

---

### Post by randy78 on 2008-11-13
Check here: [http://islandlinux.org/howto/installing-secure-ldap-openldap-ssl-ubuntu-using-self-signed-certificate]("http://islandlinux.org/howto/installing-secure-ldap-openldap-ssl-ubuntu-using-self-signed-certificate")

---

### Post by gerreth on 2008-12-09
-

---

