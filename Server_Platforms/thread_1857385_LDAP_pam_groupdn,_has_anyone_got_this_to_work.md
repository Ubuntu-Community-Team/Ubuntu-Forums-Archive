---
title: "LDAP pam_groupdn, has anyone got this to work?"
date: 2011-10-10
forum: Server Platforms
---

### Post by king756 on 2011-10-10
Hi,

I am trying to setup LDAP to restrict server access.

I want to do this by using the pam_groupdn, so only members of that group can gain access.

Using the below in '/etc/ldap.conf' anyone in the directory can log in.

```

pam_groupdn cn=web1.example.com,ou=hosts,dc=example,dc=com
pam_member_attribute member

```

The ldap directory for this group looks like

```

# Entry 1: cn=web1.example.com,ou=hosts,dc=example,dc=com
dn: cn=web1.example.com,ou=hosts,dc=example,dc=com
cn: web1.example.com
iphostnumber: *.*.*.*
member: cn=Bill,ou=people,dc=example,dc=com
objectclass: device
objectclass: extensibleObject
objectclass: ipHost
objectclass: top

```

With the above say "cn=John,ou=people,dc=example,dc=com" can still log in, pam_groupdn looks to be ignored.

If I swap the pam_lap.so and pam_unix.so in the below files the pam_groupdn works but then I am unable to log in with a local server account (I still want root access, say if ldap is down).

```

/etc/pam.d/common-account


account [success=2 new_authtok_reqd=done default=ignore]        pam_unix.so
account [success=1 default=ignore]      pam_ldap.so

account requisite                       pam_deny.so

account required                        pam_permit.so

```

```

/etc/pam.d/common-auth

auth    [success=2 default=ignore]      pam_unix.so nullok_secure
auth    [success=1 default=ignore]      pam_ldap.so debug use_first_pass

auth    requisite                       pam_deny.so

auth    required                        pam_permit.so

```

```

/etc/pam.d/common-session

# here are the per-package modules (the "Primary" block)
session [default=1]                     pam_permit.so
# here's the fallback if no module succeeds
session requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
session required        pam_unix.so
session optional                        pam_ldap.so
# end of pam-auth-update config

#Create home directory for ldap users
session required pam_mkhomedir.so skel=/etc/skel umask=0022


```

```

/etc/pam.d/common-password

password [success=2 default=ignore] pam_unix.so obscure sha512
password [success=1 user_unknown=ignore default=die] pam_ldap.so use_authtok try_first_pass

password requisite pam_deny.so
password required pam_permit.so

```

Does anyone have any experience on getting this working. From what I can see I'm not trying anything special and this shouldn't be difficult however I've been unable to figure this out or find much information from everyones favourite search engine, google.

---

### Post by king756 on 2011-10-10
Well after a 3 days of playing and a hour or so after posting this here's the solution.

Make sure /etc/pam.d/common-account looks like the below:

```

#/etc/pam.d/common-account

account sufficient pam_localuser.so
account sufficient pam_ldap.so
account required pam_deny.so

```

Local users (root) can log in and also only members specified in pam_groupdn.

---

