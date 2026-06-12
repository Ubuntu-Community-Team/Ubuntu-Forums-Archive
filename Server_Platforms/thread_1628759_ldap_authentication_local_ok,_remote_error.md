---
title: "ldap authentication local ok, remote error"
date: 2010-11-23
forum: Server Platforms
---

### Post by dhchen on 2010-11-23
Hello,
 
I followed server guide's openldap setup procedure to setup ldap authentication. (skipping tls, replication) On the server (ldap1 for example) slapd installed, authentication goes fine. I can use username stored in ldap to login. But when I setup another machine (file1 for example) to use ldap1's ldap to authenticate(of course password is correct), login always failed. file1' /var/log/auth.log tells me:
 
[FONT=Courier New]pam_ldap: error trying to bind as user "uid=user1,ou=People,dc=example,dc=com" (Invalid credentials)[/FONT]

I compared ldap1 and file1's config file, the only difference at /etc/ldap.conf is ldap's uri. /etc/ldap.secret is all the same. On both ldap1 and file1, I can use lsldap (in ldapscripts) to see user accounts. 
 
Is there any missing steps ?
 
PS: I cannot view ldap's acl setting using command provided by server guide(**ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess**), but I can assure that the admin's password is correct. Any relationships to this ?

---

### Post by numeric_way on 2010-11-24
Hi,

> **dhchen said:**
> [FONT=Courier New] "uid=user1,ou=People,dc=example,dc=com" [/FONT]

Is this the same login you use to authenticate on ldap1?

Can you also share with us your iptables configuration "sudo iptables -L" and you slapd.conf ?

---

