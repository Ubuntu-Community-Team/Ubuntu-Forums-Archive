---
title: "openldap: TLS unsupported extended operation"
date: 2014-11-02
forum: Server Platforms
---

### Post by peridian on 2014-11-02
Hi,

Ubuntu server 14.04, having trouble setting up TLS.  Have been able to run ldapsearch and perform ldapmodify updates using ldif files (adding indexes, etc).  Now trying to get TLS to work.

Tried to use the following ldif file to add TLS (p.s. I have checked read-only permissions on these certificate locations are fine for the openldap user that it runs under):

```

dn: cn=config
changetype:modify
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /usr/share/ca-certificates/extra/myca.com.crt
-
add: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ssl/mydomain/mydomain.com.key
-
add: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ssl/mydomain/mydomain.com.pem
-
add: olcTLSCipherSuite
olcTLSCipherSuite: HIGH:MEDIUM:-SSLv2
-
add: olcSecurity
olcSecurity: tls=1

```

When I run the following command, I get the following error:

```

sudo ldapmodify -x -D "cn=admin,cn=config" -W -f olcTls.ldif
Enter LDAP Password: 
modifying entry "cn=config"
ldap_result: Can't contact LDAP server (-1)

```

It looks like it connects, tries to make the modifications, and then fails.  When I use slapcat -n0, I can confirm that the cn=config database does not have the relevant olc* entries for the TLS certificates.

In my /etc/default/slapd, the line reads: *SLAPD_SERVICES="ldap://mydomain.com:389/ ldapi:/// ldaps:///"*

At first, I left my /etc/ldap/ldap.conf as:

```

URI ldap://mydomain.com/
PORT 389
BASE dc=mydomain,dc=com

```

When I run the below command, I get the following error:

```

sudo ldapsearch -x -ZZ -D "cn=admin,dc=mydomain,dc=com" -W -s sub "(objectClass=*)"
ldap_start_tls: Protocol error (2)
    additional info: unsupported extended operation

```

If I run it without the -ZZ, it works as normal.  I changed my /etc/ldap/ldap.conf to read:

```

URI ldaps://mydomain.com/
PORT 389
BASE dc=mydomain,dc=com
TLS_CACERT /usr/share/ca-certificates/extra/myca.com.crt
TLS_CERT /etc/ssl/mydomain/mydomain.com.pem
TLS_KEY /etc/ssl/mydomain/mydomain.com.key
TLS_REQCERT demand

```

I've also tried the above with the PORT set to 636.  Either way, re-running the command results in the error:

```

ldap_start_tls: Can't contact LDAP server (-1)
additional info: A TLS packet with unexpected length was received.

```

I'm fairly certain the problem is that the original ldif file did not take effect.  What have I missed from all of this?

Regards,
Rob.

---

### Post by peridian on 2014-11-03
Hi,

I've figured out that slapd was actually stopping itself part way through the process due to a checksum error on cn=config.  I used the slapcat/slapadd methodology to restore the database and get rid of the checksum issue.

It still crashes and stops part way through the ldapmodify process, showing the following error in the syslog:

```

20:41:49 user kernel: [607403.648147] slapd[7356]: segfault at 7fa9cc107008 ip 00007fa9df12fb0d sp 00007a9d992b200 error 4 in libc-2.19.so[7fa9df0b0000+1bb000]

```

Why would I get this error when trying to add TLS certificates?

Regards,
Rob.

---

### Post by peridian on 2014-11-04
Figured it out, piece by piece.


[LIST]
[*]Break the ldif file down into three pieces: a) add the certificates, b) set olcSecurity, and c) set TLSCipherSuite.
[*]a) First part succeeded no problem, however slapd then failed upon bootup.  AppArmor by default only grants slapd access to certificates in the /etc/ssl/private folder, so if you want your certificates in a different location, you have to modify the slapd permissions in AppArmor.  See: [http://serverfault.com/questions/417469/slapd-fails-to-open-tls-certificate](http://serverfault.com/questions/417469/slapd-fails-to-open-tls-certificate)
[*]b) Next part succeeded absolutely fine, can no longer ldapsearch without using startTls.
[*]c) This is the part that was killing the system in the first place, and the cause of the segfault.  I'm accustomed to openssl settings, but the build is against gnutls, which has different cipher codes.  However, there is a bug in slapd that causes it to crash completely if you try to use incorrect olcTLSCipherSuite values.  The answer was to swap to the gnutls equivalents: [FONT=arial]**[COLOR=#000000]SECURE:-VERS-SSL3.0[/COLOR]**[/FONT].  See here for the bug: [https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/1026057](https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/1026057)   See here for the gnutls cipher values: [http://www.gnu.org/software/gnutls/reference/gnutls-gnutls.html#gnutls-priority-init](http://www.gnu.org/software/gnutls/reference/gnutls-gnutls.html#gnutls-priority-init)
[/LIST]

It is all now working.  I ended up with a ldap.conf of:

```

URI ldap://mydomain.com/
PORT 389
BASE dc=mydomain,dc=com
TLS_CACERT /usr/share/ca-certificates/extra/myca.com.crt
TLS_REQCERT demand

```

Regards,
Rob.

---

