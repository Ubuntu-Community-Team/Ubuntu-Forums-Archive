---
title: "Winbind issue: &quot;groups: cannot find name for group ID&quot; -  10.04"
date: 2012-05-09
forum: Server Platforms
---

### Post by bwestover on 2012-05-09
I am running Ubuntu Server 10.04.4.

I have installed samba and winbind, and have joined the machine to join my Active Directory domain.  I want users to be able to log in with their domain accounts, but only if they belong to a specific Active Directory group.  To achieve this, I have configured the /etc/pam.d/common-auth file to include this line: 
```
auth    [success=1 default=ignore]      pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass require_membership_of=example-group
```This works, people in the group can get in, others just get an access denied. However, when users successfully log in, I see this error after the welcome message:

```
groups: cannot find name for group ID 10039
```If I use the "groups" command I can confirm that it can't resolve that one group (which btw is the one i'm requiring with PAM for login):
```
domainuser@servername:~$ groups
domain users example-domain-group1 example-domain-group2 groups: cannot find name for group ID 10039
10039
```I can see that the group is not being resolved by wbinfo either:
```
domainuser@servername:~$ wbinfo --gid-info=10039
Could not get info for gid 10039
```I can lookup other groups by name or by GID. The "groups" and "id" command list all of the other groups by name properly.

My /var/log/samba/log.winbindd log is littered with these entries:

```
winbindd/winbindd_group.c:861(getgrsid_sid2gid_recv)
  Can't find domain from name ()
```Then after a few minutes, for an unknown reason, it starts working normally. "groups", "id" and "wbinfo" all start returning the proper name for that group.

Here are the relevant winbind entries from smb.conf:

```
security = ads
idmap uid = 10000-20000
idmap gid = 10000-20000
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
winbind separator = +

```

---

