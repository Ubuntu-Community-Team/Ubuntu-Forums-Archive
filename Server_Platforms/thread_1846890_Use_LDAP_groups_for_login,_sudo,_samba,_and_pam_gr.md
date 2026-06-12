---
title: "Use LDAP groups for login, sudo, samba, and pam_groups.so"
date: 2011-09-19
forum: Server Platforms
---

### Post by linux203 on 2011-09-19
I am using OpenLDAP as an authentication/authorization directory for multiple products.  I have a group called "File Server Admins" in LDAP that is used for login, sudo, samba and file system access.  The group membership works correctly for these.  getent groups shows the memberships

A complaint is that the admins cannot access files in /var/log directly because they are not world readable.  The LDAP user is not in the adm group locally.  They must sudo before reading files.  This also complicates entering the /var/log/samba directory.

Rather than adjusting permissions on /var/log, I am trying to setup pam_groups.so.  I have made entries in /etc/security/group.conf but the LDAP user is not placed into the local group.  I changed group.conf to place a local user into a local group successfully.  I've tried using @"File Server Admins", @File Server Admins, and %"File Server Admins".  I created a temporary LDAP group without spaces in the name without success.  getent netgroup "File Server Admins" does not return anything (no error either).

Ubuntu 10.04 LTS 
libnss-ldap                           264-2ubuntu2
libpam-ldap                           184-8.2ubuntu1
slapd                                 2.4.21-0ubuntu5.5
nscd                                  2.11.1-0ubuntu7.8

/etc/security/group.conf
```
*;*;@"File Server Admins";Al0000-2400;adm
```/etc/nsswitch.conf
```

passwd: files ldap
group: files ldap
shadow: files ldap
netgroup: ldap nis
sudoers: ldap files

```/etc/pam.d/common-auth
```

auth    required                        pam_group.so use_first_pass
auth    [success=2 default=ignore]      pam_unix.so nullok_secure try_first_pass
auth    [success=1 default=ignore]      pam_ldap.so use_first_pass
auth    requisite                       pam_deny.so
auth    required                        pam_permit.so

```After searching the Internet, I have found there is a object class for  NIS groups. I don't want to maintain memberships on two groups, one for  local groups and one for everything else.  Is there a way to re-use the existing groups as  netgroups or is something broken in my config?

---

### Post by linux203 on 2011-09-27
Any ideas?

How are other people managing membership in the local adm group when using LDAP for login and sudo?

---

### Post by Nicola Quargentan on 2011-11-10
I have exactly the same problem. Did you solve the problem?

Nicola.

---

### Post by linux203 on 2011-11-10
Never did figure it out.  Didn't implement NIS groups in LDAP either.

---

### Post by Nicola Quargentan on 2011-11-12
I tried to add some lines to group.conf:
```

*;*;*;al0000-2400;dialout,plugdev

```So I was able to sets some defaults groups for all normal users.
But there still to be the problem of sudo. I add the group "admin" to LDAP server but obviously is not the same gid of local client and then does not work :(:

```

antonio@pc-rfid:~$ id
uid=1053(antonio) gid=513(Domain Users) gruppi=513(Domain Users),20(dialout),46(plugdev),117(admin),1005(plugdev),1007(dialout)

```You can see 2 time the groups dialout and plugdev because I added it's for test on LDAP server.

So I add also:

```
*;*;%admin;Al0000-2400;admin,adm
```
I want to assign a local admin and adm group at all users members of ldap admin group. But is still non work :confused: (nothing appears).
For me is sound a bit strange: I think there is a bug here.

Nicola.

---

### Post by steelsteel on 2012-02-26
Hello out there!

Exactly my problem, too (2012).
[http://forum.ubuntuusers.de/topic/alle-user-einer-ldap-gruppen-beim-login-einer-/]("http://forum.ubuntuusers.de/topic/alle-user-einer-ldap-gruppen-beim-login-einer-/")

Any help, please?

---

