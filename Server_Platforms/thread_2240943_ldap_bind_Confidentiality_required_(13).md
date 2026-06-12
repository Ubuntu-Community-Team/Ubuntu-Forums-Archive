---
title: "ldap_bind: Confidentiality required (13)"
date: 2014-08-23
forum: Server Platforms
---

### Post by sayedahmad on 2014-08-23
I want to configure ldap with ssl so I used openssl for certificate and when I enable olcSecurity tls=1 in /etc/ldap/slapd.d/cn=config.ldif and now when I try to use ldapsearch or try to login it gives this message ldap_bind: Confidentiality required (13). 
Help please

---

### Post by sandyd on 2014-08-23
> **sayedahmad said:**
> I want to configure ldap with ssl so I used openssl for certificate and when I enable olcSecurity tls=1 in /etc/ldap/slapd.d/cn=config.ldif and now when I try to use ldapsearch or try to login it gives this message ldap_bind: Confidentiality required (13). 
Help please

Looks like you are requiring connections to the server to connect using SSL/TLS

Use either the -Z flag (starttls) or ldaps:// as part of the URI

---

