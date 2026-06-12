---
title: "Installing openldap with SSL enabled"
date: 2014-07-30
forum: Server Platforms
---

### Post by ahmad6 on 2014-07-30
Hello community,

I have come to a dead end on this. I've searched all over the web for a week now and I cannot get this issue resolved, so any help is appreciated. I am running the latest version of Ubuntu server (14.04)Here is what I want to do, what I have done, and what I am getting.

I would like to install open ldap and also enable ssl to secure the connection.

I have created a self-signed cert and modified the ldap.conf file with these parameters:

```
#TLSCipherSuite HIGH:MEDIUM:-SSLv2
TLSCACertificateFile  /etc/ssl/ldap/servercer
TLSCertificateFile    /etc/ssl/ldap/server.csr
TLSCertificateKeyFile /etc/ssl/ldap/server.key
```

I also edited this file: /etc/defaults/slapd

```
SLAPD_SERVICES="ldap:/// ldaps:/// ldapi:///"
```

restarted ldap: ```
/etc/init.d/slapd restart
```

when I run this command:

```
ldapsearch -d -1 -x -H ldaps://server.domain.com -b dc=domain,dc=com
```

I get this result:

```
ldap_url_parse_ext(ldaps://server.domain.com)
ldap_create
ldap_url_parse_ext(ldaps://server.domain:636/??base)
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP server.domain.com:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying <SERVER-IP>:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
tls_write: want=117, written=117
  0000:  16 03 00 00 70 01 00 00  6c 03 03 53 d9 60 65 2c   ....p...l..S.`e,  
  0010:  13 06 1d e5 72 57 0f 5b  e5 43 45 e4 37 52 1f bb   ....rW.[.CE.7R..  
  0020:  cd 03 50 e1 71 ab e4 ee  00 2c 5e 00 00 30 00 33   ..P.q....,^..0.3  
  0030:  00 67 00 45 00 39 00 6b  00 88 00 16 00 32 00 40   .g.E.9.k.....2.@  
  0040:  00 44 00 38 00 6a 00 87  00 13 00 66 00 2f 00 3c   .D.8.j.....f./.<  
  0050:  00 41 00 35 00 3d 00 84  00 0a 00 05 00 04 01 00   .A.5.=..........  
  0060:  00 13 ff 01 00 01 00 00  0d 00 0a 00 08 04 02 04   ................  
  0070:  01 02 01 02 02                                     .....             
tls_read: want=5, got=0

TLS: can't connect: A TLS packet with unexpected length was received..
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
```

which i am not sure what it means. Now that I test the connection via LDAPS://server.domain.com:636 i get this message from my client (ldap admin) "LDAP error: Server Down!"

---

### Post by Gyokuro on 2014-08-07
Hi

Your error is already documented in: [https://wiki.debian.org/LDAP/OpenLDAPSetup](https://wiki.debian.org/LDAP/OpenLDAPSetup) and follow ==> Symptoms (round 2)

- HTH

---

