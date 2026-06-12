---
title: "remove cron from /var/log/auth.log"
date: 2009-09-03
forum: Server Platforms
---

### Post by bboston7 on 2009-09-03
Every minute cron checks for something to do and my auth.log is filled with
```
Sep  2 23:52:01 LAMPP CRON[21487]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  2 23:52:02 LAMPP CRON[21487]: pam_unix(cron:session): session closed for user root

```

This makes my logs rather hard to read when I am looking for information logged by ssh.

I know this isn't an intruder because you can only ssh into this computer from my my network and I would like my logs to be readable before I forward the port that ssh operates on.

Is there any way to make this information from cron use a different log or not show up at all?

Thanks in advance.

---

### Post by DaithiF on 2009-09-03
Hi,
edit /etc/pam.d/cron (using sudo since you need to root privileges)
and comment out the line:
```
@include common-session
```
by prepending a #

---

### Post by bboston7 on 2009-09-03
Worked like a charm.  Thank you very much

---

### Post by martinlall on 2010-11-25
But what should I exclude from that list?
/etc/pam.d/cron

#
# The PAM configuration file for the cron daemon
#

@include common-auth
session       required   pam_env.so
@include common-account
@include common-session-noninteractive
# Sets up user limits, please define limits for cron tasks
# through /etc/security/limits.conf
session    required   pam_limits.so

Thanks,
Martin

---

### Post by bio on 2010-12-27
Don't touch /etc/pam.d/cron, just  add the following line before the pam_unix.so call in /etc/pam.d/common-session-noninteractive:

```
session [success=1 default=ignore] pam_succeed_if.so service in cron quiet use_uid

```

---

### Post by alecz20 on 2011-10-24
Thanks bio, that worked for me.

---

