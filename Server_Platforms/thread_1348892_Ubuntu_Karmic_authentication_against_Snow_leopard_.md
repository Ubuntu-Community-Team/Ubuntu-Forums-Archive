---
title: "Ubuntu Karmic authentication against Snow leopard open directory server"
date: 2009-12-07
forum: Server Platforms
---

### Post by zebardy on 2009-12-07
Hi, 

I'm looking for help. I've tried to configure an installation of Karmic to authenticate against our office's open directory server running on an osx snow leopard server. Currently `getent password` show all users including those from the open directory server when running the command as both root and normal users. However authentication against the open directry users fails with the following messages in the /var/log/auth.log:-

Dec  7 22:42:05 [hostname] getent: nss_ldap: failed to bind to LDAP server ldap://server.domain.com: Invalid credentials
Dec  7 22:42:05 [hostname] getent: nss_ldap: could not search LDAP server - Server is unavailable

(I've changed the hostname and ldap url)

/etc/ldap.conf has:-

base dc=server,dc=domain,dc=com
ldap_version 3
rootbinddn cn=diradmin,dc=server,dc=domain,dc=com
bind_policy soft
pam_password md5

/etc/ldap.secret is set to the password of the diradmin user and has a permission mask of 600

/etc/pam.d/common-passwd :-

```
password sufficient pam_ldap.so md5
password required pam_unix.so nullok obscure md5
password optional pam_smbpass.so nullok use_authtok try_first_pass missingok
```

/etc/pam.d/common-auth:-

```
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.



# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]      pam_unix.so nullok_secure
auth    [success=1 default=ignore]      pam_ldap.so use_first_pass
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

/etc/pam.d/common-account:-

```
#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.
#

# here are the per-package modules (the "Primary" block)
account [success=2 new_authtok_reqd=done default=ignore]        pam_unix.so 
account [success=1 default=ignore]      pam_ldap.so 
# here's the fallback if no module succeeds
account requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

/etc/pam.d/common-session

```
#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

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
session optional                        pam_ck_connector.so nox11
# end of pam-auth-update config
```

Does anyone have any ideas where to go from here?

---

### Post by newbie-user on 2009-12-30
Here are a few resources that helped me out:

[https://help.ubuntu.com/community/OSXLDAPClientAuthentication](https://help.ubuntu.com/community/OSXLDAPClientAuthentication)
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)


You will have to change your search base in /etc/ldap.conf to include "cn=users"  ie., cn=users,dc=server,dc=domain,dc=com

Also, you'll have to edit all of the /etc/pam.d/common-* files according to the instructions in the pages listed above.

---

