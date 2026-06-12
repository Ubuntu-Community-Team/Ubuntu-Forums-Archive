---
title: "AD integration with 16.04.3"
date: 2017-09-13
forum: Server Platforms
---

### Post by thansen69 on 2017-09-13
Hi (my first post).

Relatively new to Ubuntu, but have many years of experience with different Unix flavours.

Have several 16.04.2 servers that integrates with AD-services through PAM/sssd, but new servers with 16.04.3 with same configuration does not work. Getting Access denied.

Have anyone else experienced this ?

-T

---

### Post by wonkite on 2018-05-18
yes Canonical have broken this some how, I've searched high and low cannot find any evidence that this works.

---

### Post by wonkite on 2018-05-22
For the love of God has anyone got SSSD and Active directory working, it seems to be broken by the looks of it on ubuntu 16.0.4, my test config and results are below, I'm using sssd 1.13.4 and associated components.

/etc/sssd/sssd.conf

[sssd]
config_file_version = 2
domains = buster.net
services = nss, pam
[pam]
[nss]
filter_groups = root
filter_users = root
reconnection_retries = 3
entry_cache_timeout = 3
entry_cache_nowait_percentage = 75
debug_level = 8
account_cache_expiration = 1
[domain/buster.net]
debug_level = 8
id_provider = ldap
auth_provider = ldap
access_provider = ldap
cache_credentials = false
min_id = 1000
ldap_uri = ldaps://WIN-0RV6KSDQH1I.buster.net
ldap_schema = ad
# for SID-UID mapping
ldap_id_mapping = true
# caching credentials
cache_credentials = false
entry_cache_timeout = 3
# performance
ldap_id_use_start_tls = true
ldap_service_port = 636
ldap_referrals = false
ldap_default_bind_dn = CN=administrator,DC=buster,DC=net
ldap_default_authtok_type = password
ldap_default_authtok = password
ldap_search_base = DC=buster,DC=net
ldap_tls_reqcert = demand
ldap_tls_cacert = /etc/ldap-ca/ca-cert.pem
fallback_homedir = /home/%u
ldap_user_home_directory = sAMAccountName
override_homedir = /home/%u
default_shell = /bin/bash

/etc/samba/smb.conf

[global]
workgroup = BUSTER
client signing = yes
client use spnego = yes
kerberos method = secrets and keytab
realm = BUSTER.NET
security = ads



/etc/krb5.conf

[libdefaults]
        default_realm = BUSTER.NET


# The following krb5.conf variables are only for MIT Kerberos.
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true


The results of this: I'm able to switch user to an AD user which is fine, however when I attempt to login using ssh PAM throws a wobbly!?

/var/log/auth.log generates this irritating messages

pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.1.32  user=username
May 16 23:37:12 sssd-client sshd[90834]: pam_sss(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.1.32 user=username
May 16 23:37:12 sssd-client sshd[90834]: pam_sss(sshd:auth): received for user username: 9 (Authentication service cannot retrieve authentication info)




PAM config:


::::::::::::::
common-account
::::::::::::::
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
account [success=1 new_authtok_reqd=done default=ignore]        pam_unix.so
# here's the fallback if no module succeeds
account requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
account sufficient                      pam_localuser.so
account [default=bad success=ok user_unknown=ignore]    pam_sss.so
# end of pam-auth-update config
session    required    pam_mkhomedir.so    skel=/etc/skel/    umask=0022
::::::::::::::
common-auth
::::::::::::::
#
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
auth    [success=1 default=ignore]      pam_sss.so use_first_pass
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
::::::::::::::
common-password
::::::::::::::
#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.


# Explanation of pam_unix options:
#
# The "sha512" option enables salted SHA512 passwords.  Without this option,
# the default is Unix crypt.  Prior releases used the option "md5".
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# See the pam_unix manpage for other options.


# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.


# here are the per-package modules (the "Primary" block)
password        requisite                       pam_pwquality.so retry=3
#password       [success=2 default=ignore]      pam_unix.so obscure use_authtok try_first_pass sha512
password        [success=2 default=ignore]      pam_unix.so obscure  sha512
password        sufficient                      pam_sss.so
# here's the fallback if no module succeeds
password        requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password        required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
::::::::::::::
common-session
::::::::::::::
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
# The pam_umask module will set the umask according to the system default in
# /etc/login.defs and user settings, solving the problem of different
# umask settings with different shells, display managers, remote sessions etc.
# See "man pam_umask".
session optional                        pam_umask.so
# and here are more per-package modules (the "Additional" block)
session required        pam_unix.so
session optional                        pam_sss.so
session optional        pam_systemd.so
session optional                        pam_mkhomedir.so skel=/etc/skel mask=007
# end of pam-auth-update config
::::::::::::::
common-session-noninteractive
::::::::::::::
#
# /etc/pam.d/common-session-noninteractive - session-related modules
# common to all non-interactive services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of all non-interactive sessions.
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
# The pam_umask module will set the umask according to the system default in
# /etc/login.defs and user settings, solving the problem of different
# umask settings with different shells, display managers, remote sessions etc.
# See "man pam_umask".
session optional                        pam_umask.so
# and here are more per-package modules (the "Additional" block)
session required        pam_unix.so
# end of pam-auth-update config

---

