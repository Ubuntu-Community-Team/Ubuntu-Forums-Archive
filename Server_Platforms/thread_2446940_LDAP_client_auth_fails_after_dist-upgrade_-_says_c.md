---
title: "LDAP client auth fails after dist-upgrade - says commercial cert isn't trusted"
date: 2020-07-09
forum: Server Platforms
---

### Post by nickdawson on 2020-07-09
hey folks
I did an upgrade on one of my servers to come up to 18.04. I have several other machines with virtually identical configurations. On each of them, I do LDAP authentication against an OpenLDAP server (happens to be MacOS server FWIW). All of my other machines work perfectly. 

After the upgrade, getent passwd only shows my local users. 

 ldapsearch -H ldaps://myserver.foo.bar -x -D "cn=diradmin,cn=users,dc=server,dc=domain,dc=us" -W -d1 
returns
TLS: peer cert untrusted or revoked (0x42)

The certificate in question is a valid commercial cert. 
I did a update-ca-certs and even tried copying /etc/ssl/certs from a working machine - no joy. 

The LDAP server can also respond without SSL and I tried changing /etc/ldap.conf to use ldap://myserver.foo.bar and that also doesn't work. I tried adding LDAPTLS_REQCERT=never to my ldap.conf, also no luck. 

it doesn't seem getent passwd has a verbose mode or that there are any client logs (at least that I can find)... 

Anyone have tips on troubleshooting? This box is several years old and runs some critical things... I'm almost of the point of having to do a fresh install and migrating everything which feels....daunting!

---

