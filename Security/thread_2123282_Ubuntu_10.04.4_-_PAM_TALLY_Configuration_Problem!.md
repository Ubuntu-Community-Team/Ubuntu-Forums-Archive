---
title: "Ubuntu 10.04.4 - PAM_TALLY Configuration Problem!"
date: 2013-03-07
forum: Security
---

### Post by charliemp3 on 2013-03-07
Hello All,
I'm fairly new to Ubuntu and I'm having a problem with configuring pam_tally to work properly. What I'm trying to accomplish is for this module to help me lock accounts after 3 invalid attempts, also to record these events and report them when I run the pam_tally command for each user account. This is what my common-auth file looks like right now:

**The lines highlighted in red are the ones that I have been playing with to get this to work:**

[COLOR=#ff0000]auth    required    pam_tally.so     no_magic_root     deny=3    onerr=fail lock_time=60    
acount    required    pam_tally.so[/COLOR]
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
[COLOR=#ff0000]auth    [success=2 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass[/COLOR]
# here's the fallback if no module succeeds
auth    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config


The problems are:

When these changes are in effect in the common-auth file and I purposely lock a test account after 3 invalid attempts, ALL accounts get locked, not just the test account. 

The only way to get back on the system is to hard boot and press SHIFT to go into safe mode and vi the common-auth file and comment out the lines in red. 

Once I do this I'm able to get back on the system, but if I activate these lines again, all accounts are once again locked.

Also I tried resetting the passwords some of these accounts and that did not seem to make a difference once these changes are in place in the common-auth file. 

I know that the parameters I'm including in these lines are doing something they shouldn't be but I can't tell which one. :confused:
Any help on this would be greatly appreciated. 

Thank you!

---

