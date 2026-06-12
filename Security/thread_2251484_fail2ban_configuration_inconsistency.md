---
title: "fail2ban configuration inconsistency?"
date: 2014-11-04
forum: Security
---

### Post by r.stiltskin on 2014-11-04
i'm looking at the jail.conf file created on installation of fail2ban 0.8.11-1.  In the [DEFAULT] section it says **maxretry = 3**

but further down in the file, the first entry under JAILS is the [ssh] section with **maxretry = 6** (along with a few other entries, including **enabled = true**).

What is the reason for this apparent inconsistency?

Edit: I should mention that none of the other jail sections are enabled, so it seems that both of these limits apply only to ssh and therefore it appears that 6 retries will be allowed.

---

### Post by Habitual on 2014-11-04
The reason is that any named [ jail ] that does not have a maxretry directive would use the default.
same for bantime, findtime and most other directives.
If not explicitly set in the named  [ jail ], use default values.

ssh bans out of the box (OOTB) in fail2ban is the only jail that is enabled.

Futhermore, any edits you care to make or adjust. it is suggested to use a copy of /etc/fail2ban/jail.conf as /etc/fail2ban/jail.local
This preserves your changes during upgrade|update.

fail2ban processes jail.conf first, then jail.local (if it exists) second.

---

### Post by r.stiltskin on 2014-11-04
> **Habitual said:**
> The reason is that any named [ jail ] that does not have a maxretry directive would use the default.
same for bantime, findtime and most other directives.
If not explicitly set in the named  [ jail ], use default values.


Yes, that's pretty obvious.  My point was just that, since the default configuration uses only the [ssh] jail, why would they specify a default value of 3 and then, almost 100 lines further down in the config file supersede it with a value of 6.

I'm thinking 3 is more reasonable anyway - that's what I've always used in my iptables rules to limit login attempts.  6 seems too generous especially since they configure it to ban offenders for only 10 minutes.

---

### Post by r.stiltskin on 2014-11-04
Ah, I see that the OpenSSH default value for MaxAuthTries is 6 so I guess the fail2ban developers used that value to conform with OpenSSH.

---

### Post by Habitual on 2014-11-04
> **r.stiltskin said:**
> why would they specify a default value of 3 and then, almost 100 lines further down in the config file supersede it with a value of 6.It's to illustrate that there is some flexibility in the program.
And it even says so right at the top of jail.conf
```
 24 # The DEFAULT allows a global definition of the options. They can be overridden
 25 # in each jail afterwards.
``` If they wanted it to "conform" to OpenSSH values, it would have no such option, I'd think.

---

