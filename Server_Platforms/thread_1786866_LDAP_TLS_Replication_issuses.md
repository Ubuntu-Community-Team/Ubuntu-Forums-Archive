---
title: "LDAP TLS Replication issuses"
date: 2011-06-20
forum: Server Platforms
---

### Post by VIJITH PA on 2011-06-20
Hi,

I am configuring Open LDAP TLS replication on Ubuntu 10.04 Server. the normal replication works fine without any issues. But if I enable the TLS certificates. I get the below error messages.

 

Jun 20 18:30:03 ldap-02 slapd[1114]: slap_client_connect: URI=ldap://providerip:636 Warning, ldap_start_tls failed (-1)
Jun 20 18:30:03 ldap-02 slapd[1114]: slap_client_connect: URI=ldap://providerip:636 DN="cn=xxx,dc=xxx,dc=xxx" ldap_sasl_bind_s failed (-1)
Jun 20 18:30:03 ldap-02 slapd[1114]: do_syncrepl: rid=000 rc -1 retrying

Anyone have any idea for this pls share?

with regards,
Vijith P A

---

### Post by franposta on 2011-09-12
HI,
I'm facing the same problem here, can't find to way to solve. Syncrepl won't work.

Via ldap browser I can browse the provider server (over TLS), while I can't do the same on the consumer server. 
The error i get when trying to connect to consumer server is: "Server certificate verification chain failed" (I use LBE browser).

Error messages (during syncrepl attempt):
slapd[4105]: slap_client_connect: URI=ldap://ldapprov...it Warning, ldap_start_tls failed (-1) 
slapd[4105]: slap_client_connect: URI=ldap://ldapprov.....it DN="cn=admin,dc=..it" ldap_sasl_bind_s failed (-1)
slapd[4105]: do_syncrepl: rid=000 rc -1 retrying

Any clue is welcome
Bye!

---

### Post by franposta on 2011-11-22
In my case, the problem was related to invalid certificates. I had to create consumer certificate with both options:

```
tls_www_client
tls_www_server
```

in the provider.info file.
Now consumer server acts as client for the provider (replication), and as a server for the rest of the world.
Hope this helps
Bye

---

