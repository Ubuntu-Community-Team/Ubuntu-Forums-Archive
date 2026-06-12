---
title: "TLS with ldap on Ubuntu 10.04 LTS Server not working"
date: 2011-05-23
forum: Server Platforms
---

### Post by mayankraj on 2011-05-23
Hi All,

  I have been stuck with this for quite some time now. I have installed ldap and configured it as per instructions from _[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)_

I am able to query the ldap server without forcing the TLS operation to be successful.
But with ldapsearch -d -1 -x -h servername -ZZ -b dc=example,dc=edu

I get the error

TLS: peer cert untrusted or revoked (0x42)
TLS: can't connect: (unknown error code).
ldap_err2string
ldap_start_tls: Connect error (-11)
    additional info: (unknown error code)

My /etc/ldap/ldap.conf file looks as follows

BASE dc=example,dc=edu
URI ldap://ldap.example.edu ldaps://ldap.example.edu
TLS_CERT /etc/ssl/certs/slapd-cert.pem
TLS_KEY /etc/ssl/private/slapd-key.pem
TLS_CACERT /etc/ssl/certs/slapd-cacert.pem
TLS_REQCERT allow

Any pointers would be helpful. 

Thanks
Mayank

---

### Post by luvshines on 2011-06-14
Try increasing the log level for ldapsearch command. Maybe 6 or 7

PS: Lookout for any personal information you don't want to share here before posting higher log level outputs :)

---

