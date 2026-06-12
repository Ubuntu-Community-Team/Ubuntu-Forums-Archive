---
title: "ldap server"
date: 2013-04-15
forum: Server Platforms
---

### Post by manopj1 on 2013-04-15
Hi

I user ubuntu 12.04 LTS server.I use ldap+pam for user authentication and nfs for mounting home directory. My clients are ldaptop with 11.04 .Initially wireless issue was there and now it seems to be ok.Now i am facing two issues.

1,I use autofs to mount homedir,confgiruation show below.I could not mout home dir using wild cards.Do i need to do anything on server to mount?


$ cat /etc/auto.master+auto.master/nfs/home   /etc/auto.home --timeout=120 --ghost$ cat /etc/auto.home*** -fstype=nfs,soft,intr,rsize=8192,wsize=8192,nosuid,tcp 192.168.5.250:/export/users/&**
**share -fstype=nfs,soft,intr,rsize=8192,wsize=8192,nosuid,tcp 192.168.5.250:/export/users/share**


2,My gdm hangs whenever network gets disconnected.As it is a wifi disconnection happens sometime.

below is my all configuration files

/etc/pam.d/common-session

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
session	[default=1]			pam_permit.so
# here's the fallback if no module succeeds
session	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
session	required	pam_unix.so 
session required	pam_mkhomedir.so skel=/etc/skel/
session	optional	pam_ldap.so 
session	optional	pam_ecryptfs.so unwrap
session	optional			pam_ck_connector.so nox11
# end of pam-auth-update config
#session optional	pam_mkhomedir.so skel=/etc/skel umask=077



/etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.


#passwd:         compat
#group:          compat
#shadow:         compat


passwd:         compat ldap [NOTFOUND=return] db
group:          compat ldap [NOTFOUND=return] db
shadow:         compat ldap


hosts:          files dns
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis

/etc/pam.d/common-account


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
account	[success=2 new_authtok_reqd=done default=ignore]	pam_unix.so 
account	[success=1 authinfo_unavail=1 default=ignore]	pam_ldap.so
# here's the fallback if no module succeeds
account	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config






/etc/pam.d/common-auth


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
auth	[success=4 default=ignore]			pam_unix.so nullok_secure
auth	[success=1 authinfo_unavail=ignore default=2]	pam_ldap.so use_first_pass
auth	[success=2 default=1]				pam_ccreds.so action=validate use_first_pass
auth	[default=1]					pam_ccreds.so action=store
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional			pam_ccreds.so minimum_uid=1000 action=store
auth	optional	pam_ecryptfs.so unwrap
# end of pam-auth-update config

---

