---
title: "Problem with ps showing UIDs"
date: 2008-11-04
forum: Server Platforms
---

### Post by Goobie81 on 2008-11-04
Hello all

We have configured a server (running hardy server) to authenticate via LDAP from an OS X Server like so:

/etc/pam.d/common-auth
```

auth    [success=done default=ignore]   pam_unix.so nullok_secure try_first_pass
auth    [authinfo_unavail=ignore success=1 default=2] pam_ldap.so use_first_pass
auth    [default=done]  pam_ccreds.so action=validate use_first_pass
auth    [default=done]  pam_ccreds.so action=store
auth    [default=bad]   pam_ccreds.so action=update

```
/etc/pam.d/common-session
```

session    required     pam_unix.so
session    required     pam_mkhomedir.so skel=/etc/skel/
session    optional     pam_ldap.so

```

```

account     [user_unknown=ignore authinfo_unavail=ignore default=done] pam_unix.so
account     [user_unknown=ignore authinfo_unavail=ignore default=done] pam_ldap.so
account     required       pam_permit.so

```

/etc/nsswitch.conf :
```

passwd:         files ldap [NOTFOUND=return] db
group:          files ldap [NOTFOUND=return] db
shadow: 	files ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

``` 

/etc/ldap.conf:
```

host <ldap host>
base <base dn>

timelimit 15
bind_timelimit 15
bind_policy soft
ldap_version 3
pam_password md5
nss_initgroups_ignoreusers backup,bin,daemon,dhcp,games,gnats,irc,klog,libuuid,list,lp,mail,man,messagebus,mysql,news,ntp,postfix,proxy,root,sshd,sync,sys,syslog,uucp,www-data

```

This setup works correctly with cached credentials too, should the ldap server go down:
```

# cc_dump  | grep -c ^Salted
77

```

We have two test users, testuser (UID 1091) and testuser2 (UID 1089)

```

# finger testuser          
Login: testuser       			Name: Test User
Directory: /home/testuser Shell: /bin/bash
Last login Wed Nov  5 03:29 (EST) on pts/0 from <host>
No mail.
No Plan.

# finger testuser2          
Login: testuser2       			Name: Test User 2
Directory: /home/testuser2 Shell: /bin/bash
Last login Wed Nov  5 03:30 (EST) on pts/0 from <host>
No mail.
No Plan.

```

The LDAP user's details from the LDAP server
```

# ldapsearch -h <ldap server> -x -b '<base dn>' '(uid=testuser)' 2>/dev/null | egrep '^uid:|uidNumber'
uidNumber: 1091
uid: testuser
# ldapsearch -h <ldap server> -x -b '<base dn>' '(uid=testuser2)' 2>/dev/null | egrep '^uid:|uidNumber'
uidNumber: 1089
uid: testuser2

```

And the process list for testuser shows the name properly:
```

# ps aux | grep "su - testuser"
testuser  6552  0.0  0.0   6652  2536 pts/30   S    11:59   0:00 su - testuser

```

However, a select group of users (with no discernible common ground - groups, shell, home dir etc), their processes come up with their UID instead of their name:

```

# whoami
testuser2
# ps faux | grep testuser2
1089      7808  0.0  0.0   6652  2540 pts/30   S    12:01   0:00  |       \_ su - testuser2

```

See the first column, '1089' should be **testuser2**!!

Any ideas?

Thanks!

---

### Post by Goobie81 on 2008-11-25
I have figured it out. has a maximum of 8 letters for the username. If the username is longer than 8 letters it just shows the UID.

---

