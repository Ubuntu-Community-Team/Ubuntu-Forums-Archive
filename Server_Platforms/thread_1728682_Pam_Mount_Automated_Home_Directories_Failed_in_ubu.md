---
title: "Pam_Mount Automated Home Directories Failed in ubuntu 10.04"
date: 2011-04-14
forum: Server Platforms
---

### Post by joven15 on 2011-04-14
Anyone help me how to configure Pam_Mount im using Likewise-open

this is my pam.d configuration

**/etc/pam.d/common-auth**

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
auth    [success=3 default=ignore]    pam_krb5.so minimum_uid=1000
auth    [success=2 default=ignore]    pam_unix.so nullok_secure try_first_pass
auth    [success=1 default=ignore]    pam_lsass.so try_first_pass
# here's the fallback if no module succeeds
auth    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required            pam_permit.so

# and here are more per-package modules (the "Additional" block)
auth    optional    pam_mount.so 
auth    optional            pam_smbpass.so migrate

# end of pam-auth-update config
[B]
/etc/pam.d/common-session[/B]

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
session    [default=1]            pam_permit.so
# here's the fallback if no module succeeds
session    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
session    optional            pam_krb5.so minimum_uid=1000
session    required    pam_unix.so 
session    optional    pam_mount.so 
session    optional    pam_ck_connector.so nox11
session    sufficient    pam_lsass.so
session    sufficient    pam_localuser.so
# end of pam-auth-update config

**/etc/pam.d/common-account**

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
account    [success=3 new_authtok_reqd=done default=ignore]    pam_unix.so 
account    [success=ok new_authtok_reqd=ok default=ignore]        pam_lsass.so unknown_ok
account    [success=1 new_authtok_reqd=done default=ignore]    pam_lsass.so 

# here's the fallback if no module succeeds
account    requisite            pam_deny.so

# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account sufficient            pam_winbind.so
account    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
account    required            pam_krb5.so minimum_uid=1000
# end of pam-auth-update config

/////////////////////////////////
**i follow this guide [http://ubuntuforums.org/showthread.php?t=1636500&highlight=pam_mount](http://ubuntuforums.org/showthread.php?t=1636500&highlight=pam_mount)**

<mntcheck>mount</mntcheck>

<pmvarrun>pmvarrun -u %(USER) -o %(OPERATION)</pmvarrun>

<volume options="uid=%(USER),gid=root,dir_mode=0700,nosuid,nodev" user="*" fsype="cifs" server="192.168.101.6" path="itdept$" mountpoint="/home/local/PMCGROUP/%(USER)/Zfiles" credentials="/home/pmcspare/.smbcredentials/" />

////////////////////////////////////////////////////

im using Ubuntu 10.04 Lucid Lynx  Desktop

AD Joining Sucessful and when i login using AD Account sucess i dont see any home or sharing file directory there :(

Thanks i hope someone help me :(

---

