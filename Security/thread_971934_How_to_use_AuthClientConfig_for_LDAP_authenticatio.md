---
title: "How to use AuthClientConfig for LDAP authentication _and_ local users"
date: 2008-11-05
forum: Security
---

### Post by javahollic on 2008-11-05
Hi,
I installed 'auth-client-config' on server Ibex x86_64, and after a few tweaks finally have LDAP authentication, wonderful.  But.  now local users, eg database accounts, no longer 'exist'.  I'm not a PAM expert, have fiddled, have failed, to enable this with judicious spreading of 'sufficient pam_unix.so'.  I would have thought this is a common requirement and would be a great 'bundled' example.

Any PAM savvy peeps know how to enable local user lookups and authentication in _addition_ to ldap lookup/auth (use /etc/passwd /etc/shadow)

Thanks,
andy. :confused:

heres config:
```

[ldap_test]
nss_passwd=passwd: files ldap compat
nss_group=group: files ldap compat
nss_shadow=shadow: files ldap compat
nss_netgroup=netgroup: nis
pam_auth=auth       required     pam_env.so
        auth       sufficient   pam_unix.so <=== try to do this first
	auth       sufficient   pam_unix.so likeauth nullok
	auth       sufficient   pam_ldap.so use_first_pass
	auth       required     pam_deny.so
pam_account=account    sufficient   pam_unix.so
	account    sufficient   pam_unix.so  <=== try to do this first
	account    sufficient   pam_ldap.so
	account    required     pam_deny.so
pam_password=password   required     pam_cracklib.so difok=2 minlen=8 dcredit=2 ocredit=2 retry=3
	password   sufficient   pam_unix.so nullok md5 shadow use_authtok
	password   sufficient   pam_ldap.so use_first_pass
	password   required     pam_deny.so
pam_session=session    required     pam_limits.so
	session    required     pam_unix.so
	session    optional     pam_ldap.so

```

---

### Post by lemming465 on 2008-11-17
Have you checked /etc/nsswitch.conf to make sure it says stuff like:
```
passwd: files ldap
group: files ldap
```

---

### Post by javahollic on 2008-11-18
Hi thanks for that. yes indeed, that's what I was missing.  Its now working a treat :popcorn:

---

