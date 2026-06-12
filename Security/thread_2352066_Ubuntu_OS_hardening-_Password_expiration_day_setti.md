---
title: "Ubuntu OS hardening- Password expiration day settings (version 14.0.4.3)"
date: 2017-02-09
forum: Security
---

### Post by makauser on 2017-02-09
Dear Concern,

We want to implement following OS hardening feature in below version in Ubuntu. Request to share us necessary plan.

amirislam@blnidapp03:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty

1. Password expiration day settings change (PASS_MAX_DAYS 90, PASS_MIN_DAYS 0, PASS_MIN_LEN 8, PASS_WARN_AGE 7).
 2. Session timeout after 5 minutes.

With Best Regards,
Md. Abdullah-Al Kauser

---

### Post by TheFu on 2017-02-09
chage

Session timeout is a different thing.

14.04.3 is not currently supported.  Need to move to 14.04.5 to be supported.  This is your largest security issue.

---

### Post by oldfred on 2017-02-09
Duplicate thread. Closed.

See 
[https://ubuntuforums.org/showthread.php?t=2352065](https://ubuntuforums.org/showthread.php?t=2352065)

TheFu also gave answer in other thread, so not merged.

---

