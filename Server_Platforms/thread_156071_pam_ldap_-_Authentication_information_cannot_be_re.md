---
title: "pam_ldap - Authentication information cannot be recovered"
date: 2006-04-06
forum: Server Platforms
---

### Post by Xer0 on 2006-04-06
Hi,
I'm trying to setup LDAP Client Authentication on my ubuntu box to a slapd service running on a gentoo server. As far I can tell, I can login and sudo with LDAP users, but I can't change my password (using passwd). I can su to users that only exist on LDAP (but not locally).

```

$ getent passwd | grep xavier
xavier:x:1000:100:xavier:/home/xavier:/bin/bash
$ cat /etc/passwd | grep xavier
$ passwd
Enter login(LDAP) password: <incorrect pwd>
LDAP Password incorrect: try again
Enter login(LDAP) password: <correct pwd>
passwd: Authentication information cannot be recovered

```

Hopefully handy configuration files:
```
# /etc/nsswitch.conf
passwd:         files ldap
group:          files ldap
shadow:         files ldap

hosts:          files dns
services:       files
networks:       files
protocols:       files
rpc:       files
ethers:       files

netgroup:       nis

```

```
# /etc/pam.d/common-auth
auth    sufficient      pam_ldap.so
auth    required      pam_unix.so likeauth nullok shadow use_first_pass

# /etc/pam.d/common-account
account sufficient      pam_ldap.so
account required        pam_unix.so

# /etc/pam.d/common-password
password   sufficient   pam_ldap.so use_authtok
password   required   pam_unix.so nullok obscure min=4 max=8 md5

# /etc/pam.d/common-session
session         sufficient        pam_ldap.so
session         required        pam_unix.so
session         required        pam_mkhomedir.so skel=/etc/skel/ umask=0

```

Any ideas?

---

### Post by Xer0 on 2006-04-12
Need to remove "use_authtok" from from common-password. I think it is needed/helpful when using pam_cracklib, but am not sure.

```

# /etc/pam.d/common-password
password   sufficient   pam_ldap.so
password   required   pam_unix.so nullok obscure min=4 max=8 md5
```

---

### Post by tekknokrat on 2007-12-19
> **Xer0 said:**
> Need to remove "use_authtok" from from common-password. I think it is needed/helpful when using pam_cracklib, but am not sure.

```

# /etc/pam.d/common-password
password   sufficient   pam_ldap.so
password   required   pam_unix.so nullok obscure min=4 max=8 md5
```

I had the same problem and your solution worked :popcorn:

---

