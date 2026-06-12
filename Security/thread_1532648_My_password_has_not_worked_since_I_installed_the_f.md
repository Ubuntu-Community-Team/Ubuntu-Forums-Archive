---
title: "My password has not worked since I installed the fingerprint reader"
date: 2010-07-16
forum: Security
---

### Post by marticc on 2010-07-16
Hi, I tried to install fprint (to use the fingerprint reader on my laptop) as mentioned here ( [http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018) )
; and after editing the common-auth file (no error message was shown); the system hasn't accepted my password when I tried to start synaptic, and then when I restarted the laptop and tried to login (I have 3 accounts and I can not login using any of them). And now I can't start Ubuntu (I can only access to my files using the live CD)

I would be really thankful if you could help me. Thanks.

PS1: I am using Ubuntu 10.04 on a Lenovo Intel dual core system.
PS2: When i installed the fprint I chose the fingerprint to be suffcient
PS·: This is my common auth file:

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.)
.  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional	pam_ecryptfs.so unwrap
# end of pam-auth-update config

---

