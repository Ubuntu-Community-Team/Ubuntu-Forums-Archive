---
title: "Problem with PAM and LDAP"
date: 2011-02-04
forum: Server Platforms
---

### Post by jtwood on 2011-02-04
I already know of a work around to fix this problem, but I guess my question is why is this not working as expected?

I am using a Windows Server 2008 R2 Active Directory for authentication.

I have run auth-client-config for the ldap profile and pam-auth-update.

When running getent passwd, I get a list of both the local users and the users in the active directory (with populated information in the Unix schema extension).

When running getent group I get a list of both the local groups and the groups in the active directory (with populated information in the Unix schema extension).

Interestingly enough, though, when I run su DOMAINUSER, after the prompt for the password I get an authentication error.  In /var/log/auth.log I can see an entry with pam_ldap: missing "host" in file "/etc/ldap.conf".

The SRV records in the DNS servers resolve correctly.  I've checked this with nslookup and I have seen the records within my zone file.  Obviously if the ldap.conf file is working with getent and the ldap server is resolving from the SRV records, it is working fine.

The interesting part is that the Windows Server 2008 R2 AD machine shows in the event viewer that there was a successful authentication, yet the Ubuntu box says no.

When I add the host within the ldap.conf file, everything works...getent and the actual authentication, either initial login or su.

Any ideas?

Getent works with the host declaration commented, but su and login does  not.  When I uncomment both work.  My hope was to be able to use the SRV  records in DNS to determine the host, allowing me to have my Primary and Backup ADs and any changes and additions be propagated to DNS rather than a dozen conf files.

ldap.conf
```
base dc=domain,dc=internal
#host ares.domain.internal
ldap_version 3
binddn cn=ldapsearch,cn=users,dc=domain,dc=internal
bindpw mypassword

rootbinddn cn=administrator,cn=users,dc=domain,dc=internal

pam_member_attribute uniquemember

nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_attribute uid sAMAccountName
nss_map_attribute homeDirectory UnixHomeDirectory
nss_map_attribute shadowLastChange pwdLastSet
nss_map_objectclass posixGroup group
nss_map_attribute uniqueMember member
pam_login_attribute sAMAccountName
pam_filter objectclass=User
pam_password ad

pam_groupdn DomainAdmins

nss_initgroups_ignoreusers backup,bin,daemon,games,gnats,irc,landscape,libuuid,list,lp,mail,man,news,proxy,root,sync,sys,syslog,uucp,www-data
```nsswitch.conf
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd: files ldap
group: files ldap
shadow: files ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup: nis
```common-account
```
# here are the per-package modules (the "Primary" block)
account    [success=2 new_authtok_reqd=done default=ignore]    pam_unix.so 
account    [success=1 default=ignore]    pam_ldap.so 
# here's the fallback if no module succeeds
account    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```common-auth
```
# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_ldap.so use_first_pass
# here's the fallback if no module succeeds
auth    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```common-session
```
# here are the per-package modules (the "Primary" block)
session    [default=1]            pam_permit.so
# here's the fallback if no module succeeds
session    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
session    required    pam_unix.so 
session    optional            pam_ldap.so 
# end of pam-auth-update config

```

---

### Post by jtwood on 2011-02-04
I don't know if anybody can confirm this, but I would assume that getent  is making calls from nss_ldap and pam through both nss_ldap and  pam_ldap.
  
  If nss_ldap supports DNS SRV records and pam_ldap does not support DNS  SRV records, then this all makes sense.  Looking through strace -e open  it looks like this could be a possibility.  It seems that su DOMAINUSER  seems use both nss_ldap and pam_ldap, which would explain the partial  authentication with the Active Directory server and the Authentication  failure within Ubuntu.  At some point when the lookup in the LDAP  directory on the AD is happening, I would guess that the bind is  successful through nss_ldap but the authentication fails in pam because  of the lack of support for using a dns srv record for the host lookup in  pam_ldap.
 
 Wireshark somewhat confirms this.  I ran it with the host defined and  without the host defined in ldap.conf doing an su DOMAINUSER and could  see the same exchange happen between the two machines for the first  part, but there was nothing in the second part when the host was  undefinied in ldap.conf
  
  As I said, this is my theory so far.  I've Google searched it to no  avail.  I can't seem to find anything definitive about whether nss_ldap  or pam_ldap supports SRV DNS records or whether something else is going on entirely.
 
 Thanks in advance.

--I've actually confirmed that the current implementation of pam_ldap does not support DNS SRV Records through [http://www.padl.com/](http://www.padl.com/) pam_ldap documentation...of course I am sure that this may be subject to change on future releases.--

---

