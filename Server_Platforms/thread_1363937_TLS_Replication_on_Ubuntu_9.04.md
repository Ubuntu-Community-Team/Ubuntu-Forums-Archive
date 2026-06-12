---
title: "TLS Replication on Ubuntu 9.04"
date: 2009-12-25
forum: Server Platforms
---

### Post by ananthaprasada.jps on 2009-12-25
Hi 

I am configuring TLS replication between 2 openldap servers. Master and Slave. I have used the below URL to configure the TLS replication. Without TLS replication everything works fine and the data replication is also very fast. 

[https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html)

But If i do the TLS replication, I get lot errors. like as below. 

Dec 26 02:49:54 ldapserver slapd[2571]: slap_client_connect: URI=ldap://ldapserver Warning, ldap_start_tls failed (-11)
Dec 26 02:49:54 ldapserver slapd[2571]: slap_client_connect: URI=ldap://ldapserver DN="cn=admin,dc=embargo,dc=slb,dc=com" ldap_sasl_bind_s failed (-1)
Dec 26 02:49:54 ldapserver slapd[2571]: do_syncrepl: rid=003 retrying (1 retries left)
Dec 26 02:49:55 ldapserver slapd[2571]: slap_client_connect: URI=ldap://ldapserver Warning, ldap_start_tls failed (-11)
Dec 26 02:49:55 ldapserver slapd[2571]: slap_client_connect: URI=ldap://ldapserver DN="cn=admin,cn=config" ldap_sasl_bind_s failed (-1)
Dec 26 02:49:55 ldapserver slapd[2571]: do_syncrepl: rid=001 retrying (1 retries left)
Dec 26 02:50:01 ldapserver /USR/SBIN/CRON[2985]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 26 02:50:29 ldapserver slapd[2571]: slap_client_connect: URI=ldap://ldapslave Warning, ldap_start_tls failed (-11)
Dec 26 02:50:29 ldapserver slapd[2571]: slap_client_connect: URI=ldap://ldapslave Warning, ldap_start_tls failed (-11)
Dec 26 02:50:29 ldapserver slapd[2571]: slap_client_connect: URI=ldap://ldapslave DN="cn=admin,cn=config" ldap_sasl_bind_s failed (-1)
Dec 26 02:50:29 ldapserver slapd[2571]: slap_client_connect: URI=ldap://ldapslave DN="cn=admin,dc=embargo,dc=slb,dc=com" ldap_sasl_bind_s failed (-1)
Dec 26 02:50:29 ldapserver slapd[2571]: do_syncrepl: rid=004 retrying (1 retries left)
Dec 26 02:50:29 ldapserver slapd[2571]: do_syncrepl: rid=002 retrying (1 retries left)



Please Help, 

Regards,
Anjan

---

### Post by franposta on 2011-09-12
Hi,
I know that this is an old thread but I'm facing the same problem here with ubuntu server 10.10.
Has anyone solved this issue?
Thank you!

---

