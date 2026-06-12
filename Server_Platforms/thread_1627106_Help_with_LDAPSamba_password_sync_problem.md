---
title: "Help with LDAP/Samba password sync problem"
date: 2010-11-21
forum: Server Platforms
---

### Post by skiani on 2010-11-21
Hi,

Pulling my hair out on this one. I'm trying to get and LDAP configured Samba PDC to password sync such when a windowsXP user can change password the LDAP entry for userPassword need to be SHA or MD5 (compatibility with google doc's API). Not matter what I try the userPassword is SSHA. Here are what I think are the relevant smb.conf entry's:

```
  unix password sync = no
  ldap passwd sync = yes
#  passwd program = /usr/bin/passwd %u
#   passwd program = /usr/sbin/smbldap-passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes

```
And here's my ldap.conf file:

```
uri ldapi:///
ldap_version 3
rootbinddn cn=admin,dc=mydomain,dc=local
pam_password md5
```

I'm running ubuntu 10.10 64bit

thanks,

---

