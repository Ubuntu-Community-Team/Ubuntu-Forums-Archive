---
title: "LDAP Auth PAM Issue"
date: 2008-07-15
forum: Server Platforms
---

### Post by elesueur on 2008-07-15
Hi,

I have setup hardy to authenticate via our ssl enabled LDAP server.

It works using public key authentication remotely via ssh, but I can't login locally.

Here are my current configs

/etc/ldap.conf and /etc/ldap/ldap.conf
```

BASE dc=ertos,dc=nicta,dc=com,dc=au
URI ldaps://ldap.ertos.nicta.com.au/
TLS_CACERT /etc/ldap/keys/cacert.pem
bind_policy soft

```

/etc/libnss-ldap.conf
```

uri		ldaps://ldap.ertos.nicta.com.au/
base		dc=ertos,dc=nicta,dc=com,dc=au
bind_policy	soft

```

/etc/nssswitch.conf
```

passwd:         files ldap
group:          files ldap
shadow:         files ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

/etc/pam_ldap.conf
```

uri ldaps://ldap.ertos.nicta.com.au/
base ou=Accounts,dc=ertos,dc=nicta,dc=com,dc=au
scope one
pam_password exop
pam_filter objectclass=account
bind_policy soft
ssl on

```

/etc/pam.d/common-account
```

account [perm_denied=bad acct_expired=bad success=ok default=ignore]\
                        pam_ldap.so
account required        pam_unix.so

```

/etc/pam.d/common-auth
```

auth    sufficient      pam_ldap.so
auth    required        pam_unix.so nullok_secure try_first_pass

```

/etc/pam.d/common-password
```

password	sufficient	pam_ldap.so
password	required	pam_unix.so nullok obscure min=4 max=8 md5

```

/etc/pam.d/common-session
```

session sufficient      pam_ldap.so
session required        pam_unix.so

```

ldapsearch returns the correct data
getent passwd returns the correct data
getent group returns the correct data

home directories are automounted via nfs.

Can anyone see any issues with the way it's setup?

Any help is appreciated!

---

### Post by elesueur on 2008-07-16
ok... I think I've figured out the problem...

for some reason, pam_ldap isn't searching on the specified tree:

```

base ou=Accounts,dc=ertos,dc=nicta,dc=com,dc=au

```

In my client auth logs, I see it's trying to bind as 

"cn=Full Name,ou=People,dc...."

rather than

"uid=username,ou=Accounts,dc...."

Can anyone think of a reason why this might be happening if the base is correctly specified in the pam_ldap.conf file?

---

### Post by elesueur on 2008-07-16
solution:

set the following directives in ldap.conf and libnss-ldap.conf

nss_base_passwd
nss_base_group
nss_base_shadow

it appears that pam_ldap.conf is no longer required...

---

