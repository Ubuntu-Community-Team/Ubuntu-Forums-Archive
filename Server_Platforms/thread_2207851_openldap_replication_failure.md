---
title: "openldap replication failure"
date: 2014-02-25
forum: Server Platforms
---

### Post by bluethundr2 on 2014-02-25
Hello,

 I've followed a really great guide in the ubuntu docs on how to get openldap functioning. So far, I've been happy to see that OpenLdap is functioning on 2 nodes (using ubuntu 12.04). Both are running with TLS (using START/TLS) and are searchable. 

[https://help.ubuntu.com/12.10/serverguide/openldap-server.html](https://help.ubuntu.com/12.10/serverguide/openldap-server.html)


However I am now up to the openldap replication section and I'm unable to get the two to communicate. The query the docs give you to verify that openldap replication is working is the following:

Provider (ldap01):
```

root@ldap01:~/ldap# ldapsearch -z1 -LLLQY EXTERNAL -H ldapi:/// -s base contextCSN
dn:

```

Consumer (ldap02):
```

root@ldap02:~/ldap# ldapsearch -z1 -LLLQY EXTERNAL -H ldapi:/// -s base contextCSN
dn:

```


As you can see there is no response from this query on either server. 

In the logs on the consumer (ldap02) I see the following:
```

root@ldap02:~/ldap# tail /var/log/syslog
Feb 25 16:00:15 ip-172-31-5-73 slapd[6437]: conn=1008 op=0 BIND authcid="gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth" authzid="gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth"
Feb 25 16:00:15 ip-172-31-5-73 slapd[6437]: conn=1008 op=0 BIND dn="gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth" mech=EXTERNAL sasl_ssf=0 ssf=71
Feb 25 16:00:15 ip-172-31-5-73 slapd[6437]: conn=1008 op=0 RESULT tag=97 err=0 text=
Feb 25 16:00:15 ip-172-31-5-73 slapd[6437]: conn=1008 op=1 SRCH base="" scope=0 deref=0 filter="(objectClass=*)"
Feb 25 16:00:15 ip-172-31-5-73 slapd[6437]: conn=1008 op=1 SRCH attr=contextCSN
Feb 25 16:00:15 ip-172-31-5-73 slapd[6437]: conn=1008 op=1 SEARCH RESULT tag=101 err=0 nentries=1 text=
Feb 25 16:00:15 ip-172-31-5-73 slapd[6437]: conn=1008 op=2 UNBIND
Feb 25 16:00:15 ip-172-31-5-73 slapd[6437]: conn=1008 fd=16 closed
Feb 25 16:00:55 ip-172-31-5-73 slapd[6437]: slap_client_connect: URI=ldap://ldap01.example.com DN="cn=admin,dc=example,dc=com" ldap_sasl_bind_s failed (49)
Feb 25 16:00:55 ip-172-31-5-73 slapd[6437]: do_syncrepl: rid=000 rc 49 retrying

```

It looks as if the consumer is having trouble authenticating with the provider. I'm just wondering if I've missed a step in the guide or if the guide itself missed a step. Or if there are any other steps I can take to try and troubleshoot this problem.

Thanks

---

