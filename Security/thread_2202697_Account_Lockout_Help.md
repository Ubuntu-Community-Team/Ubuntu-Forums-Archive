---
title: "Account Lockout Help"
date: 2014-01-30
forum: Security
---

### Post by vendethiel on 2014-01-30
I'm trying to setup an ubuntu 12.04 workstation to lock an account after 5 failed login attempts. What I've done was add the following line to /etc/pam.d/common-auth:

```
 auth required pam_tally.so onerr=fail deny=5 unlock_time=900
```

This works, however, when the screen locks, i'm unable to log back in without clicking switch user and then logging in as you normally would. However from the lock screen even when I type the correct password in it states its incorrect.

Any ideas? Am I not configuring this correctly? Below is what my /etc/pam.d/common-auth file looks like:

```
## /etc/pam.d/common-auth - authentication settings common to all services
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
auth required pam_tally.so onerr=fail deny=5 unlock_time=900
# here are the per-package modules (the "Primary" block)
auth    [success=1 default=ignore]      pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional                        pam_cap.so
# end of pam-auth-update config


```


Thanks!

---

### Post by vendethiel on 2014-01-30
Just realized I may have posted this in the wrong forum...

---

### Post by vendethiel on 2014-02-02
I think this may be my answer:

[http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/](http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/)

---

### Post by Bucky Ball on 2014-02-02
Is it your answer?

---

### Post by vendethiel on 2014-02-03
No, still having issues. Will look into faillog.

---

### Post by vendethiel on 2014-02-03
Got it. pam_tally.so is apparently obsolete in 12.04. I have to use pam_tally2.so.

I had to add the following lines to the top of my "/etc/pam.d/common-auth" file:

```
auth    required    pam_tally2.so deny=5 onerr=fail unlock_time=900
account     required      pam_tally2.so

```

Now to tweak it so it won't lock root!

Source:
[http://linux.die.net/man/8/pam_tally2](http://linux.die.net/man/8/pam_tally2)
[http://www.nsa.gov/ia/_files/os/redhat/NSA_RHEL_5_GUIDE_v4.2.pdf](http://www.nsa.gov/ia/_files/os/redhat/NSA_RHEL_5_GUIDE_v4.2.pdf)

---

