---
title: "LDAP auth for ProFTPd"
date: 2011-05-20
forum: Server Platforms
---

### Post by ZuOverture on 2011-05-20
Hello again.

I'm a bit stuck with using my Samba4 PDC - it should authorize access to the FTP shares, though, it desperately resists.

What was made:
1. apt-get install proftpd-basic proftpd-mod-ldap ldap-utils
2. Uncommented and added to proftpd.conf
#
# Alternative authentication frameworks
#
Include /etc/proftpd/ldap.conf
# This is required to use both PAM-based authentication and local passwords
AuthOrder mod_ldap.c
RequireValidShell off

3. ldap.conf
```
$ cat ldap.conf
#
# Proftpd sample configuration for LDAP authentication.
#
# (This is not to be used if you prefer a PAM-based LDAP authentication)
#

<IfModule mod_ldap.c>
#
# This is used for ordinary LDAP connections, with or without TLS

LDAPServer localhost:389
LDAPDNInfo "cn=**admin**,cn=Users,dc=mydomain,dc=dyndns,dc=com" "**adminpass**"
LDAPDoAuth on "cn=Users,dc=mydomain,dc=dyndns,dc=com" (&(sAMAccountName=%u)(objectclass=user))

LDAPDoUIDLookups on "cn=Users,dc=mydomain,dc=dyndns,dc=com"
LDAPDoGIDLookups on "cn=Groups,,dc=mydomain,dc=dyndns,dc=com"

LDAPDefaultUID  1 **<-don't know if it should correlate with real IDs, but without these params logon fails**
LDAPDefaultGID  10

LDAPAttr homeDirectory profilePath

# To be set on only for LDAP/TLS on ordinary port, for LDAP+SSL see below
#LDAPUseTLS on
#

#
# This is used for encrypted LDAPS connections
#
#LDAPServer ldaps://ldap.example.com
#LDAPDNInfo "cn=admin,dc=example,dc=com" "admin_password"
#LDAPDoAuth on "dc=users,dc=example,dc=com"
#
</IfModule>
```

4. Sample of AD user container:
```
$ ldapsearch -h 192.168.0.200 -W -x -D "cn=**myfullusername**,cn=Users,dc=mydomain,dc=dyndns,dc=com" -b "cn=Users,dc=mydomain,dc=dyndns,dc=com" sAMAccountName=**myusername**
Enter LDAP Password:
# extended LDIF
#
# LDAPv3
# base <cn=Users,dc=mydomain,dc=dyndns,dc=com> with scope subtree
# filter: sAMAccountName=**myusername**
# requesting: ALL
#

# **myfullusername**, Users, mydomain.dyndns.com
dn: CN=**myfullusername**,CN=Users,DC=mydomain,DC=dyndns,DC=com
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: user
cn: **myfullusername**
sn: **mysurname**
givenName: **myname**
instanceType: 4
whenCreated: 20110517102324.0Z
displayName: **myfullusername**
uSNCreated: 3478
name: **myfullusername**
objectGUID:: *someguid*
badPwdCount: 0
codePage: 0
countryCode: 0
badPasswordTime: 0
lastLogoff: 0
lastLogon: 0
primaryGroupID: 513
objectSid:: *somesid*
accountExpires: 9223372036854775807
logonCount: 0
sAMAccountType: 805306368
objectCategory: CN=Person,CN=Schema,CN=Configuration,DC=mydomain,DC=dyndns,DC=com
pwdLastSet: 129501014040000000
userAccountControl: 66048
userPrincipalName: **myusername**@mydomain.dyndns.com
sAMAccountName: **myusername**
profilePath: \\PDC1.mydomain.dyndns.com\profiles\**myusername**
whenChanged: 20110518114553.0Z
userParameters:: IAAgACAAIAAgACAAIAAgACAAIAAgACAAIAAgACAAIAAgACAAIAAgACAAIAAgA
 CAAIAAgACAAIAAgACAAIAAgACAAIAAgACAAIAAgACAAIAAgACAAIAAgACAAIAAgACAAUAAEABoACA
 ABAEMAdAB4ABMAZgEnAFAAcuBlAHMAZQBgAHQANTUiZTBxYjAYAAgAAQBDAHQAeABDAGYAZwBGAGw
 AYQBnAHMAMQAwMGYwZTBmNxIACAABAEMAdAB4AFMAaABwAGQAbhB3ADAwMDAwMDAwKgACAAEAQwB0
 AHgATQBpAG4ARQBuAGMAcgB5AHAAdABpAG8AbgBMAGUAdgBlAGwAMDE=
uSNChanged: 3742
distinguishedName: CN=**myfullusername**,CN=Users,DC=mydomain,DC=dyndns,DC=com

# search result
search: 2
result: 0 Success

# numResponses: 2
# numEntries: 1
```

5. As far, as I can go with FileZilla, according to /var/log/proftpd/proftpd.log
```
May 20 16:30:43 PDC1 proftpd[2122] 192.168.0.200: ProFTPD 1.3.3d (maint) (built Mon Mar 28 2011 21:54:58 UTC) standalone mode STARTUP
May 20 16:30:45 PDC1 proftpd[2125] 192.168.0.200 (192.168.0.125[192.168.0.125]): FTP session opened.
May 20 16:30:45 PDC1 proftpd[2125] 192.168.0.200 (192.168.0.125[192.168.0.125]): **myusername** chdir("\\PDC1.mydomain.dyndns.com\profiles\**myusername**"): No such file or directory
May 20 16:30:45 PDC1 proftpd[2125] 192.168.0.200 (192.168.0.125[192.168.0.125]): FTP session closed.
```
Directory exists and keeps my roaming profile.

Any suggestions?

---

### Post by ZuOverture on 2011-05-22
Back again - still there.

---

### Post by ZuOverture on 2011-05-23
:? Well, thanks to everyone being involved in this lively discussion. Solved.

---

### Post by james_xxx on 2011-10-24
Sort of uncool that no one else got involved in this thread to help you out.

Also sort of equally uncool that you marked it as solved, without mentioning how you solved it.

If you ever get a chance, please let us (me) know!

---

