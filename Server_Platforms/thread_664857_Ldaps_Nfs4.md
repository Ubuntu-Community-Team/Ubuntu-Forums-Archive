---
title: "Ldaps Nfs4"
date: 2008-01-11
forum: Server Platforms
---

### Post by kuba-g on 2008-01-11
Hi!

I have Debian server with ldap (without ssl) and nfs4. For my clients I am using Kubuntu/Ubuntu. Now I want to add ssl ca to my ldap server.

I have already configurated my ldap server:

```

macserv:~# openssl s_client -connect macserv:636 -showcerts
....
....
....
....
---
No client certificate CA names sent
---
SSL handshake has read 1657 bytes and written 316 bytes
---
New, TLSv1/SSLv3, Cipher is AES256-SHA
Server public key is 1024 bit
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1
    Cipher    : AES256-SHA
    Session-ID: 37637DA8738E9F783893DFE9F78ED183DF62466119E968DD645AACD645
    Session-ID-ctx:
    Master-Key: 04AC17C3EB10AEF0CA36222546CB9658227F2AE93F0F62466119E968DD645AA873E93F01C448E93F0FE9AE93F01C448450D84
    Key-Arg   : None
    Start Time: 1200086107
    Timeout   : 300 (sec)
    Verify return code: 19 (self signed certificate in certificate chain)


```

636 port is listening:
```

macserv:~# netstat -ltnp | grep :636
tcp        0      0 0.0.0.0:636             0.0.0.0:*               LISTEN     3226/slapd
tcp6       0      0 :::636                  :::*                    LISTEN     3226/slapd


```

and now the ubuntu client, see ldapsearch:

```

ubuntu:~# ldapsearch -x -b dc=macserv,dc=lo5 -H 'ldaps://macserv.lo5'
...
...
(long list)
...
# search result
search: 2
result: 0 Success

# numResponses: 109
# numEntries: 108

```

I have modified configs on Ubuntu:
1. /etc/ldap/ldap.conf
```

# $OpenLDAP: pkg/ldap/libraries/libldap/ldap.conf,v 1.9 2000/09/04 19:57:01 kurt Exp $
#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

BASE    dc=macserv, dc=lo5
URI     ldaps://192.168.5.17:636

#SIZELIMIT      12
#TIMELIMIT      15
#DEREF          never
TLS_REQCERT allow
TLS_CACERT /etc/ldap/cacert.pem

```

and both /etc/libnss-ldap.conf , /etc/pam_ldap.conf

```

.......
# OpenLDAP SSL mechanism
# start_tls mechanism uses the normal LDAP port, LDAPS typically 636
ssl start_tls
ssl on
........

```

then
```

/etc/init.d/nscd restart 

```

and:
```

ubuntu:~# getent group
.......
.......
Debian-exim:x:102:
mlocate:x:103:
ssh:x:104:
user:x:1000:

```

so I don't have ldap auth :(

My question is why?? What I've done wrong?

Thanks for help...

---

### Post by gpredrag on 2008-01-11
In both /etc/libnss-ldap.conf , /etc/pam_ldap.conf you have turned on "ssl on" and "ssl start tls".
If both options are used it defaults to "ssl start_tls" so pam and nsswitsh use start tls over port 389 instead of raw ldap over encrypted ssl connection on 636. It would be nicer for you to chose one or another.
Also in both /etc/libnss-ldap.conf , /etc/pam_ldap.conf there is important setting:
"tls_cacertfile" that should point to your CA certificate, because pam and nsswitch default to "tls_checkpeer yes" (another setting in those files), and peer verification fails if Ubuntu machines don't have CA certificate available.
getent failure means that it's nsswitch that is failing (for now).
Are there any messages in syslog, auth.log?

---

### Post by kuba-g on 2008-01-11
auth.log

```

Jan 11 23:17:01 ubuntu CRON[4193]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 11 23:17:01 ubuntu CRON[4193]: pam_unix(cron:session): session closed for user root
Jan 11 23:18:14 ubuntu nscd: nss_ldap: could not connect to any LDAP server as cn=admin,dc=macserv,dc=lo5 - Can't contact LDAP server
Jan 11 23:18:14 ubuntu nscd: nss_ldap: failed to bind to LDAP server ldaps:///192.168.5.17:636: Can't contact LDAP server
Jan 11 23:18:14 ubuntu nscd: nss_ldap: reconnecting to LDAP server...
Jan 11 23:18:14 ubuntu nscd: nss_ldap: could not connect to any LDAP server as cn=admin,dc=macserv,dc=lo5 - Can't contact LDAP server
Jan 11 23:18:14 ubuntu nscd: nss_ldap: failed to bind to LDAP server ldaps:///192.168.5.17:636: Can't contact LDAP server
Jan 11 23:18:14 ubuntu nscd: nss_ldap: reconnecting to LDAP server (sleeping 1 seconds)...
Jan 11 23:18:15 ubuntu nscd: nss_ldap: could not connect to any LDAP server as cn=admin,dc=macserv,dc=lo5 - Can't contact LDAP server
Jan 11 23:18:15 ubuntu nscd: nss_ldap: failed to bind to LDAP server ldaps:///192.168.5.17:636: Can't contact LDAP server
Jan 11 23:18:15 ubuntu nscd: nss_ldap: could not search LDAP server - Server is unavailable
Jan 11 23:18:15 ubuntu nscd: nss_ldap: could not connect to any LDAP server as cn=admin,dc=macserv,dc=lo5 - Can't contact LDAP server
Jan 11 23:18:15 ubuntu nscd: nss_ldap: failed to bind to LDAP server ldaps:///192.168.5.17:636: Can't contact LDAP server
Jan 11 23:18:15 ubuntu nscd: nss_ldap: reconnecting to LDAP server...
Jan 11 23:18:15 ubuntu nscd: nss_ldap: could not connect to any LDAP server as cn=admin,dc=macserv,dc=lo5 - Can't contact LDAP server
Jan 11 23:18:15 ubuntu nscd: nss_ldap: failed to bind to LDAP server ldaps:///192.168.5.17:636: Can't contact LDAP server
Jan 11 23:18:15 ubuntu nscd: nss_ldap: reconnecting to LDAP server (sleeping 1 seconds)...
Jan 11 23:18:16 ubuntu nscd: nss_ldap: could not connect to any LDAP server as cn=admin,dc=macserv,dc=lo5 - Can't contact LDAP server
Jan 11 23:18:16 ubuntu nscd: nss_ldap: failed to bind to LDAP server ldaps:///192.168.5.17:636: Can't contact LDAP server
Jan 11 23:18:16 ubuntu nscd: nss_ldap: could not search LDAP server - Server is unavailable
Jan 11 23:22:02 ubuntu sshd[4182]: pam_env(ssh:setcred): Unable to open env file: /etc/environment: No such file or directory
Jan 11 23:49:12 ubuntu sshd[4206]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jan 11 23:49:12 ubuntu sshd[4206]: pam_ldap: reconnecting to LDAP server...
Jan 11 23:49:12 ubuntu sshd[4206]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jan 11 23:49:12 ubuntu sshd[4206]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jan 11 23:49:12 ubuntu sshd[4206]: pam_ldap: reconnecting to LDAP server...
Jan 11 23:49:12 ubuntu sshd[4206]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jan 11 23:49:12 ubuntu sshd[4206]: Accepted password for root from 192.168.5.17 port 50419 ssh2
Jan 11 23:49:12 ubuntu sshd[4206]: pam_env(ssh:setcred): Unable to open env file: /etc/environment: No such file or directory
Jan 11 23:49:12 ubuntu sshd[4208]: pam_unix(ssh:session): session opened for user root by root(uid=0)
Jan 11 23:49:12 ubuntu sshd[4208]: pam_env(ssh:setcred): Unable to open env file: /etc/environment: No such file or directory
Jan 11 23:50:52 ubuntu getent: nss_ldap: could not connect to any LDAP server as cn=admin,dc=macserv,dc=lo5 - Can't contact LDAP server
Jan 11 23:50:52 ubuntu getent: nss_ldap: failed to bind to LDAP server ldaps:///192.168.5.17:636: Can't contact LDAP server
Jan 11 23:50:52 ubuntu getent: nss_ldap: reconnecting to LDAP server...
Jan 11 23:50:52 ubuntu getent: nss_ldap: could not connect to any LDAP server as cn=admin,dc=macserv,dc=lo5 - Can't contact LDAP server
Jan 11 23:50:52 ubuntu getent: nss_ldap: failed to bind to LDAP server ldaps:///192.168.5.17:636: Can't contact LDAP server
Jan 11 23:50:52 ubuntu getent: nss_ldap: reconnecting to LDAP server (sleeping 1 seconds)...
Jan 11 23:50:53 ubuntu getent: nss_ldap: could not connect to any LDAP server as cn=admin,dc=macserv,dc=lo5 - Can't contact LDAP server
Jan 11 23:50:53 ubuntu getent: nss_ldap: failed to bind to LDAP server ldaps:///192.168.5.17:636: Can't contact LDAP server
Jan 11 23:50:53 ubuntu getent: nss_ldap: could not search LDAP server - Server is unavailable

```

it looks horrible :D:D

so I've changed my configs
```

# OpenLDAP SSL mechanism
# start_tls mechanism uses the normal LDAP port, LDAPS typically 636
#ssl start_tls
ssl on

# OpenLDAP SSL options
# Require and verify server certificate (yes/no)
# Default is to use libldap's default behavior, which can be configured in
# /etc/openldap/ldap.conf using the TLS_REQCERT setting.  The default for
# OpenLDAP 2.0 and earlier is "no", for 2.1 and later is "yes".
tls_checkpeer yes

# CA certificates for server certificate verification
# At least one of these are required if tls_checkpeer is "yes"
tls_cacertfile /etc/ldap/cacert.pem
#tls_cacertdir /etc/ssl/certs

``` 

I have copied  cacert.pem from my server but I don't know it is a good move.
Client is still not working..

---

### Post by gpredrag on 2008-01-11
Client still can't validate server certificate. In order for client to validate server's certificate, client must have in possession certificate of the CA that signed server's certificate (that should be corrected now).
BUT, there are additional checks that server's certificate must pass. For example, "subject" of the  certificate (to whom is certificate issued) should be DNS name of the server. And if that is set, then you should connect to server by it's DNS name and not by it's IP address. (unless you have also set subject altname in certificate).
So, if certificate is issued to "my.server.tld" your url should be ldaps://my.server.tld:636 and not ldaps://192.168.5.17:636.
You have been able see subject of the certificate with that:
```

macserv:~# openssl s_client -connect macserv:636 -showcerts

```

right after subject=CN=my.server.tld.......
So you either correct that url, or turn tls_checkpeer to "no".
Is that selfsigned server certificate? Seems that it is not well known that both in Debian and Ubuntu there is tinyca2  program for no-fuss-real-CA-and-real-server certificates.

---

### Post by kuba-g on 2008-01-11
```

macserv:~# openssl s_client -connect macserv:636 -showcerts
CONNECTED(00000003)
depth=1 /C=PL/ST=Slask/O=V Liceum/OU=lo5/CN=macserv.lo5/emailAddress=kuba.g4@gmail.com
verify error:num=19:self signed certificate in certificate chain
verify return:0
---
...............................

```

I have already changed 192.168.5.17 to macserv.lo5 but still nothing

tinyca is graphical program? my server do not have X.org installed, and for now I am using ssh connection for clients and server ;/

---

### Post by gpredrag on 2008-01-12
I am pretty sure that certificate verification is your problem. Try setting tls_checkpeer to "no" temporarily to see if that works.

[http://www.openldap.org/faq/data/cache/185.html](http://www.openldap.org/faq/data/cache/185.html) has more on ldap and tls

Yes tinyca is gtk program, but in doesn't have (should not, really) be installed on production servers. It should be installed on trusted administrative workstation. One should use it to create local CA certificate which should be distributed to all computers.
Than you create server's certificate and private key, sign the certificate and install them on server.

---

### Post by kuba-g on 2008-01-15
SSL works thank you

But, I have another problem. I have added kerberos5 support to nfsv4, and now ldap users can't access their home directories ;/

---

### Post by gpredrag on 2008-01-15
Please provide more information.
How did you arranged for users to obtain tickets. does that work? Do users have their tickets?
How did you arranged for home folders to be mounted?
There is Howto in Ubuntu community documentation that covers NFS4, have you checked that?
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)
I haven't actually followed that (I use automount) but I believe there are some good points there.

---

### Post by kuba-g on 2008-01-18
Ok 

I have already configured NFSv4 with KRB5: [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) <-- from this howto
 I have also already configured Krb5 for server and client, and it works. There are several problems that I have:

1. My ldapusers don't have access to their home directories ( I am mounting /home via Nfsv4 + Krb5) should I create krb5 account for each user?

2. I do not have an integration of Ldap and krb5, I can't find any usefull howto or article for this

3. I want for my ldap and krb5 users one authentification and one password, pam + krb5? I also cannot find any Howto

Thanks for help...

---

### Post by gpredrag on 2008-01-19
All  your nfs4 mounting users should also be kerberos principals, and should have their kerberos tickets after login. It means that yous should use LDAP for nsswitch only, and kerberos for authentication. That means leaving pam_ldap for libpam_heimdal (I use that) or libpam_krb5. Both come with documentation in /usr/share/doc/whatever after install, and If you have managed to use pam_ldap you will have no problem using these. Also in gutsy there is auth-client-config packages for managing pam and nsswitch.  That package comes with template for kerberos authentication (but without ldap nsswitch)  in /etc/auth-client-config/profile.d wich you can use to create template for your need (with ldap nsswitch).
As for keberos+LDAP  integration people usually use Heimdal kerberos,([http://www.pdc.kth.se/heimdal/](http://www.pdc.kth.se/heimdal/)) which can store it's principals in LDAP. That way one can create LDAP user, add kerberos attributes and set kerberos password. There is also smbk5pwd overlay ("plugin") for slapd which can synchronize samba and kerberos password, (but it must be built manualy) .But, if you already have kerberos infrastructure  without LDAP in place, I don't know  simple way of transffering it in LDAP (short of recreating kerberos realm from start). Heimdel's site has info on this. Without kerberos LDAP integration you would have to create kerberos principal for a user, and then create LDAP object for nsswitch for that user.  If you don't have that many users that also might work.

---

### Post by kuba-g on 2008-01-20
ehh

I do not have time for changes ;/ I have only one week ;/

I have MIT implementation for krb, ldaps and nfs4, so maybe better for me is to use ldaps + afs, what do you think?

---

