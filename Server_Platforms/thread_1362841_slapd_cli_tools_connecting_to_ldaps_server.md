---
title: "slapd cli tools connecting to ldaps server"
date: 2009-12-23
forum: Server Platforms
---

### Post by box2 on 2009-12-23
I have set up openldap (slapd) pretty successfully on Hardy (8.04).  I have generated a self-signed certificate and am now running slapd in ssl only mode (only on port 636).  I can connect to it fine using from my workstation using Apache Directory Studio (to browse/modify the ldap tree), but the command line tools on the server itself don't work anymore.

For example: 
$ ldapsearch -xLLL -v
ldap_initialize( <DEFAULT> )
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

I have edited my /etc/ldap/ldap.conf to include:

```

URI   ldaps://localhost
TLS_REQCERT     allow

```

(an nmap scan shows that slapd is in fact listening on localhost as expected, so I'm assuming this should be ok).  I have tested from the local machine that it can pick up an SSL connection which works fine too:

$ openssl s_client -connect localhost:636 -showcerts
CONNECTED(00000003)
(goes on to describe my certificate)


Any help with getting my CLI tools to work again?

---

### Post by box2 on 2009-12-24
Wewt seems I've stumped a few people.  How about starting smaller.

Anyone have experience with if an SSL cert has to be EXACTLY right for ldap tools to verify the server?  Such as if they are trying to connect to a server by IP address, does the Common Name on the cert have to be an IP address?

-a

---

