---
title: "NSS LDAPS authtentication not working in 10.04.1"
date: 2010-09-13
forum: Server Platforms
---

### Post by halfmanhalfpint on 2010-09-13
Using NSS LDAPS authentication on our Ubuntu 8.04 servers for a number of years.
Have tried to get this working with 10.04.1 Server, but it fails to
contact the LDAP server.
Am using the command "getent passwd" to test this, It should display all
LDAP password entries but doesn't. This error appears in /var/log/auth.log:

Sep 13 15:16:45 server1 getent: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Sep 13 15:16:45 server1 getent: nss_ldap: failed to bind to LDAP server ldaps://10.10.35.3: Can't contact LDAP server
Sep 13 15:16:45 server1 getent: nss_ldap: could not search LDAP server - Server is unavailable

To set this up, installed the packages libnss-ldap and libpam-ldap.
Created /etc/ldap.conf containing the following:

base ou=customers,dc=mydom,dc=net
uri ldaps://10.10.34.20 ldaps://10.10.35.3
rootbinddn uid=xxxx,ou=jim,ou=fred,dc=mydom,dc=net
scope sub
timelimit 4
bind_timelimit 4
ssl on
tls_checkpeer no
tls_cacertfile /usr/local/ssl/certs/rootca.pem

/etc/nsswitch.conf for passwd and group is:

passwd:         compat ldap
group:          compat ldap

This is identical to our 8.04 setup. Is it broken in 10.04, or am
I missing something?

---

### Post by halfmanhalfpint on 2010-09-13
By the way, it works with LDAP, just not LDAPS.

---

### Post by Kent Asplund on 2010-10-12
I am noticing the same thing. It works with ldap but not ldaps.

Connecting with luma or jxplorer works.

---

### Post by Kent Asplund on 2011-02-26
Probable cause of failure could be missing certificate on server (/etc/ldap/cacert.pem)

I have not personally tested it, tip came from "pappa razi"

---

### Post by Caudovittatus on 2011-02-26
Hi, I had a similar problem (full details in this thread: [http://ubuntuforums.org/showthread.php?t=1692655](http://ubuntuforums.org/showthread.php?t=1692655))

For me the problem was resolved by editing /etc/ldap/ldap.conf and adding the line:
TLS_CACERT <path_to_my_CA_certificate>

It turned out that while I'd imported the certificate into my external LDAP clients (Apache Directory Studio, JXplorer), the one on the localhost had no idea where to look; adding the above line solved the issue.

---

