---
title: "LDAP and SSL on 8.04"
date: 2008-05-09
forum: Server Platforms
---

### Post by djorgens on 2008-05-09
Hi all,

I've been looking at this for the past couple of weeks now and I'm having some real trouble trying to find any info.

I had an LDAP server running with SSL/TLS using OpenSSL under 7.10, but after doing a fresh install of 8.04, SSL/TLS just refused to work at all.

I found some information on the web that suggests that OpenLDAP in now linked against gnuTLS and looking at the dependencies for ldap-utils shows that it requires libgnutls13 instead of libssl. Also, all the options for TLS setup have disappeared from the configs, so the Ubuntu devs obviously know about it too.

That being the case, has anybody any documentation for how to set up an LDAP server with SSL/TLS using gnuTLS, including setting up the certificates and (more importantly really) the ldap.conf config for the server and client?

Thanks,

DJ

---

### Post by djorgens on 2008-05-13
Seriously, does nobody have any information on this at all?

---

### Post by bluefrog on 2008-05-13
have a look at openldap.org and samba.org

---

### Post by cdenley on 2008-05-30
Not only does the openldap user need read access to any SSL files referenced in slapd.conf, but apparently...
> 
the private key must not be protected with a password

I found that in the man page. Instead of changing the permissions on apache's certificate and key and removing the key's password, I created a seperate certificate.

---

### Post by adamos on 2008-06-04
Can you provide more information? I cant make it to work openldap with gnutls. If you have the solution please provide it here.

---

### Post by cdenley on 2008-06-04
Simple, remove the password from the key (assuming that is the problem). I think it would be something like this
```

mv ssl.key ssl.key.pass
openssl rsa -in ssl.key.pass -out ssl.key

```
I didn't want to remove the password from my certificate signed by a CA, so I created a new one and signed it myself.

---

