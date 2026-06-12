---
title: "Ubuntu 8.10 Openldap Client Config"
date: 2009-01-06
forum: Server Platforms
---

### Post by joemanz on 2009-01-06
Hi everyone,

I'm having some issue with OpenLdap client on the Ubuntu 8.10. I've followed the LDAPClientAuthentication here [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) and I'm getting this error in the /var/log/auth.log

```

Jan  5 19:23:16 rtplxdt01 gdm[5042]: pam_unix(gdm:auth): check pass; user unknown
Jan  5 19:23:16 rtplxdt01 gdm[5042]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= 

```

Here are the configurations for the PAM via auth-client-config:

```

[ldap]
nss_passwd=passwd: files ldap
nss_group=group: files ldap
nss_shadow=shadow: files ldap
nss_netgroup=netgroup: files ldap
pam_auth=auth   required        pam_env.so
        auth    sufficient      pam_unix.so likeauth nullok
        auth    required        pam_group.so use_first_pass
        auth    sufficient      pam_ldap.so use_first_pass
        auth    required        pam_deny.so
pam_account=account    sufficient   pam_unix.so
        account    sufficient   pam_ldap.so
        account    required     pam_deny.so
pam_password=password   required     pam_cracklib.so difok=2 minlen=8 dcredit=2 ocredit=2 retry=3
        password   sufficient   pam_unix.so nullok md5 shadow use_authtok
        password   sufficient   pam_ldap.so use_first_pass
        password   required     pam_deny.so
pam_session=session    required     pam_limits.so
        session required        pam_mkhomedir.so skel=/etc/skel/
        session    required     pam_unix.so
        session    optional     pam_ldap.so

```

I've also edit the /etc/security/group.conf to add assign local group to domain (LDAP) users:
```

*; *; *; Al0000-2400; users,adm,dialout,fax,cdrom,floppy,tape,audio,dip,video,plugdev,scanner,fuse

```

If anyone has come across this same issue, please let me know. Thanks in advance.


Joe

---

### Post by windependence on 2009-01-07
Check your /etc/shadow to see if there is a user missing or disabled. In a terminal type:

```
 sudo /etc/shadow
```

The only user with a uid of 0 is should be root.

-Tim

---

### Post by joemanz on 2009-01-07
I'm using an ldap user and I don't think it would be in the /etc/shadow file.
I can actually SSH into the machine using an ldap user but I can't logon via GDM login. I'm guessing that I should tweak the /etc/pam.d/gdm for this to work.  Any ideas anyone?

-Joe

---

### Post by joemanz on 2009-01-07
Ops, double post.. :)

---

