---
title: "postfix: no greylisting after positive spf check (Ubuntu 12.04.2 LTS)"
date: 2013-08-22
forum: Server Platforms
---

### Post by 7-launchpad-1 on 2013-08-22
Hi everyone!

I'm running a postfix as my MTA. I check incoming mail for a valid spf record and greylist as well.

I do the spf checks with postfix-policyd-spf-perl and greylisting with postgrey.

My main.cf is configured like this:

```
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, check_policy_service unix:private/policy-spf, check_policy_service inet:127.0.0.1:10023
```

Obviously, I have also created an entry in my master.cf for the spf check:

```
policy-spf  unix  -       n       n       -       -       spawn     user=nobody argv=/usr/sbin/postfix-policyd-spf-perl

```

Everything runs OK so far. The only thing I'd like to change was this: if a spf check returns a positive result (e.g. ```
postfix/policy-spf[30254]: Policy action=PREPEND Received-SPF: pass
```) I would like to omit the greylisting. Is there a way to do so?

Regards
  Steffen

---

