---
title: "OpenLDAP error: ldap_bind: Confidentiality required (13)"
date: 2007-03-30
forum: Server Platforms
---

### Post by taenus on 2007-03-30
I'm trying to port my SLES LDAP configuration over to Ubuntu.  I'm fairly sure my new server is configured correctly, I think I have some trouble with my client config.  I can use ldapsearch and slapcat to pull the (empty) LDAP database, but when I try to do an ldapadd, I get the following:

> [FONT="Courier New"]
# ldapadd -x -H ldap://localhost -D cn=admin,dc=me,dc=org -W -f core.ldif
ldap_bind: Confidentiality required (13)
[/FONT]

Here is my slapd.conf:
> [FONT="Courier New"]
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
schemacheck     on
pidfile         /var/run/slapd/slapd.pid
argsfile        /var/run/slapd.args
loglevel        0
modulepath      /usr/lib/ldap
moduleload      back_bdb
TLSCACertificateFile    /etc/ldap/cacert.pem
TLSCertificateFile      /etc/ldap/servercrt.pem
TLSCertificateKeyFile   /etc/ldap/serverkey.pem
backend         bdb
checkpoint 512 30
database        bdb
suffix          "dc=me,dc=org"
rootdn          "cn=admin,dc=me,dc=org"
rootpw          {SSHA}asdfasdfasdfasdf
directory       "/var/lib/ldap"
index           objectClass eq
lastmod         on
access to attrs=userPassword
        by dn="cn=admin,dc=me,dc=org" write
        by anonymous auth
        by self write
        by * none
access to dn.base="" by * read
access to *
        by dn="cn=admin,dc=me,dc=org" write
        by * read
[/FONT]

And my ldap.conf:
> [FONT="Courier New"]
BASE            dc=me,dc=org
URI             ldap://localhost
TLS_CACERT      /etc/ldap/cacert.pem
ssl             start_tls
[/FONT]

---

### Post by BoneKracker on 2007-04-17
I haven't played with ldap in a long time, but since no one else has answered...

I think it's asking you for the password.  You may have stored the password in the client config in the past and don't have it there now.  You can also give the password in the command line I think.

---

