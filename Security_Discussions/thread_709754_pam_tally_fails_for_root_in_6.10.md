---
title: "pam_tally fails for root in 6.10"
date: 2008-02-27
forum: Security Discussions
---

### Post by mark.tunnell on 2008-02-27
As soon as I add any pam_tally entry to /etc/pam.d/common-auth on my 6.10 servers I stop being able to SSH in as root.  My password authenticates, but the connection immediately closes.  Other accounts function just fine.  Only root has this issue.  The same configuration works fine for root on 7.10.

Here's my common.auth:
auth    required        pam_unix.so nullok_secure
auth    required        pam_tally.so deny=3 unlock_time=60

Any ideas?  Is this a bug in 6.10?

---

