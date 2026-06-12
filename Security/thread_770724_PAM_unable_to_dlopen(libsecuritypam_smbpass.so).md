---
title: "PAM unable to dlopen(/lib/security/pam_smbpass.so)"
date: 2008-04-27
forum: Security
---

### Post by Kschikan on 2008-04-27
After upgrading to 8.04, I've noticed some issues. One of which is the following which keeps showing up in my /var/log/auth.log

Apr 27 10:17:01 Griffin CRON[6040]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 27 10:17:01 Griffin CRON[6040]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Apr 27 10:17:01 Griffin CRON[6040]: PAM adding faulty module: /lib/security/pam_smbpass.so
Apr 27 10:17:01 Griffin CRON[6040]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 27 10:17:01 Griffin CRON[6040]: pam_unix(cron:session): session closed for user root


A quick check shows that pam_smbpass.so does not exist in /lib/security/
Does anybody know where I can find this file, or otherwise resolve the error?

---

### Post by Monicker on 2008-04-27
I think you are seeing the results of this bug:

[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990")

I see the error in my own logs for HH, and have noticed it in other logs which have been posted to the forums.

---

### Post by Kschikan on 2008-04-27
Thanks for the quick reply, Monicker.

---

