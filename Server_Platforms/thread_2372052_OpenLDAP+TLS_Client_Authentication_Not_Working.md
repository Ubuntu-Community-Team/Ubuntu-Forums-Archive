---
title: "OpenLDAP+TLS Client Authentication Not Working"
date: 2017-09-21
forum: Server Platforms
---

### Post by sciens-sciencia on 2017-09-21
I am attempting to configure LDAP+STARTTLS and its gone wrong somewhere....

Environment:

domain - test.domain
subnet - 10.0.10.0/24

hostname  -  IP
TestDesktop  106
dhcp         200
ldap         210
ns           250
gateway      254


DNS and DHCP are for dynamic DNS updates via dhcp.d and bind9.

LDAP is the LDAP server, running slapd: 2.4.42+dfsg-2ubuntu3.2 and is  populated with a test user with a password. I have installed  phpldapadmin and i can view, edit and add entries to LDAP without issue  using STARTTLS.

I followed [This LDAP+TLS tutorial]("https://www.digitalocean.com/community/tutorials/how-to-encrypt-openldap-connections-using-starttls") to configure a fresh LDAP server, [This LDAP client tutorial]("https://www.server-world.info/en/note?os=Ubuntu_16.04&p=openldap&f=3") to configure the client and [This tutorial]("https://www.server-world.info/en/note?os=Ubuntu_16.04&p=openldap&f=4") to add TLS to the client.

Im now getting the following logs when i attempt to login:

_**Server**_

```


     root@ldap:/home/sysadmin# cat /var/log/syslog 

Sep 20 21:28:21 ldap slapd[12559]: conn=1000 fd=13 ACCEPT from IP=10.0.10.106:56988 (IP=0.0.0.0:389)
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=0 EXT oid=1.3.6.1.4.1.1466.20037
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=0 STARTTLS
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=0 RESULT oid= err=0 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 fd=13 TLS established tls_ssf=128 ssf=128
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=1 BIND dn="cn=admin,dc=test,dc=domain" method=128
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=1 BIND dn="cn=admin,dc=test,dc=domain" mech=SIMPLE ssf=0
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=1 RESULT tag=97 err=0 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=2 SRCH base="dc=test,dc=domain" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=testuser))"
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=2 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=2 SEARCH RESULT tag=101 err=0 nentries=1 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=3 SRCH base="dc=test,dc=domain" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=testuser))"
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=3 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=3 SEARCH RESULT tag=101 err=0 nentries=1 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 fd=21 ACCEPT from IP=10.0.10.106:56990 (IP=0.0.0.0:389)
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=0 EXT oid=1.3.6.1.4.1.1466.20037
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=0 STARTTLS
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=0 RESULT oid= err=0 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 fd=21 TLS established tls_ssf=128 ssf=128
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=1 BIND dn="cn=admin,dc=test,dc=domain" method=128
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=1 BIND dn="cn=admin,dc=test,dc=domain" mech=SIMPLE ssf=0
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=1 RESULT tag=97 err=0 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=2 SRCH base="dc=test,dc=domain" scope=2 deref=0 filter="(uid=testuser)"
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=2 SEARCH RESULT tag=101 err=0 nentries=1 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=3 BIND anonymous mech=implicit ssf=0
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=3 BIND dn="cn=Test User,dc=test,dc=domain" method=128
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=3 BIND dn="cn=Test User,dc=test,dc=domain" mech=SIMPLE ssf=0
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=3 RESULT tag=97 err=0 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=4 BIND anonymous mech=implicit ssf=0
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=4 BIND dn="cn=admin,dc=test,dc=domain" method=128
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=4 BIND dn="cn=admin,dc=test,dc=domain" mech=SIMPLE ssf=0
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=4 RESULT tag=97 err=0 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=4 SRCH base="dc=test,dc=domain" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=testuser))"
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=4 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=4 SEARCH RESULT tag=101 err=0 nentries=1 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=5 SRCH base="dc=test,dc=domain" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=testuser))"
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=5 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=5 SEARCH RESULT tag=101 err=0 nentries=1 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=6 SRCH base="dc=test,dc=domain" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=testuser))"
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=6 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 op=6 SEARCH RESULT tag=101 err=0 nentries=1 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 op=5 UNBIND
Sep 20 21:28:21 ldap slapd[12559]: conn=1001 fd=21 closed
Sep 20 21:28:21 ldap slapd[12559]: conn=1000 fd=13 closed (connection lost)
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 fd=13 ACCEPT from IP=10.0.10.106:56992 (IP=0.0.0.0:389)
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=0 EXT oid=1.3.6.1.4.1.1466.20037
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=0 STARTTLS
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=0 RESULT oid= err=0 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 fd=13 TLS established tls_ssf=128 ssf=128
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=1 BIND dn="cn=admin,dc=test,dc=domain" method=128
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=1 BIND dn="cn=admin,dc=test,dc=domain" mech=SIMPLE ssf=0
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=1 RESULT tag=97 err=0 text=
Sep 20 21:28:21 ldap slapd[12559]: connection_input: conn=1002 deferring operation: binding
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=2 SRCH base="dc=test,dc=domain" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=testuser))"
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=2 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=2 SEARCH RESULT tag=101 err=0 nentries=1 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=3 SRCH base="dc=test,dc=domain" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=testuser))"
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=3 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=3 SEARCH RESULT tag=101 err=0 nentries=1 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=4 SRCH base="dc=test,dc=domain" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=testuser))"
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=4 SEARCH RESULT tag=101 err=0 nentries=1 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=5 SRCH base="dc=test,dc=domain" scope=2 deref=0 filter="(&(objectClass=posixGroup)(|(memberUid=testuser)(uniqueMember=cn=test user,dc=test,dc=domain)))"
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=5 SRCH attr=gidNumber
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=5 SEARCH RESULT tag=101 err=0 nentries=0 text=
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=6 SRCH base="dc=test,dc=domain" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=testuser))"
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=6 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass
Sep 20 21:28:21 ldap slapd[12559]: conn=1002 op=6 SEARCH RESULT tag=101 err=0 nentries=1 text= 

```[U][B]

Client[/B][/U]

```

  root@TestDesktop:/home/sysadmin# cat /var/log/auth.log 

Sep 18 19:36:31 TestDesktop lightdm: nss_ldap: reconnecting to LDAP server...
Sep 18 19:36:31 TestDesktop lightdm: nss_ldap: reconnected to LDAP server ldap://ldap.test.domain/ after 1 attempt
Sep 18 19:36:31 TestDesktop lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=testuser
Sep 18 19:36:31 TestDesktop lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Sep 18 19:36:31 TestDesktop lightdm: PAM adding faulty module: pam_kwallet.so
Sep 18 19:36:31 TestDesktop lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Sep 18 19:36:31 TestDesktop lightdm: PAM adding faulty module: pam_kwallet5.so
Sep 18 19:36:31 TestDesktop lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "testuser" 

```

All assistance is greatly appreciated!

---

