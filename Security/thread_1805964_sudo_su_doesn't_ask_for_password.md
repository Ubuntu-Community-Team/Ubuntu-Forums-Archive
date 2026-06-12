---
title: "sudo su doesn't ask for password"
date: 2011-07-16
forum: Security
---

### Post by tivrfoa on 2011-07-16
Ubuntu 10.04 LTS - the Lucid Lynx 64 bits

when I type sudo su, it goes direct to root without asking for password. :/

How can I fix this?

/etc/pam.d/common-auth
```
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
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional			pam_cap.so 
# end of pam-auth-update config
```

/etc/pam.d/sudo
```
#%PAM-1.0

@include common-auth
@include common-account

session required pam_permit.so
session required pam_limits.so
```

---

### Post by bodhi.zazen on 2011-07-16
sudo is configured by /etc/sudoers 

Also there is a grace period after using sudo, you can reset it as well with:

```
sudo -k
```

See

[http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tivrfoa on 2011-07-17
> **bodhi.zazen said:**
> sudo is configured by /etc/sudoers 
I commented this line:ALL ALL=NOPASSWD: ALL

and now it's working. =)

do you know why it was configured this way?
can some software that I installed be the cause of this problem?

---

### Post by bodhi.zazen on 2011-07-17
> **tivrfoa said:**
> do you know why it was configured this way?
can some software that I installed be the cause of this problem?

Not that I know of, as far as I know sudoers is manually configured.

---

### Post by tivrfoa on 2011-07-17
> **bodhi.zazen said:**
> Not that I know of, as far as I know sudoers is manually configured.
maybe it's how sudoers is configured by default in Ubuntu Server edition ...

---

### Post by bodhi.zazen on 2011-07-17
> **tivrfoa said:**
> maybe it's how sudoers is configured by default in Ubuntu Server edition ...

Not that I know of.

---

