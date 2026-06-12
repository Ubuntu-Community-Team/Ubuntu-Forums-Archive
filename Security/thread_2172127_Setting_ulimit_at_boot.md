---
title: "Setting ulimit at boot?"
date: 2013-09-03
forum: Security
---

### Post by Hungry Man on 2013-09-03
I'd like to set up a ulimit at bootup for a specific user, so that the user can only run a single process. Best way to do this?

---

### Post by Amorphous Serendipity on 2013-10-06
Hi Hungry Man,

I know this isn't a direct answer to your  question, but it may be a good idea to work with pam_limits for a bit  more flexibility.

Below are some links that should get you started:
[http://linux.die.net/man/8/pam_limits](http://linux.die.net/man/8/pam_limits)
[http://linux.die.net/man/5/limits.conf](http://linux.die.net/man/5/limits.conf)
[http://www.linux-pam.org/Linux-PAM-html/sag-pam_limits.html](http://www.linux-pam.org/Linux-PAM-html/sag-pam_limits.html)

I hope this helps!

---

### Post by Hungry Man on 2013-10-06
Unfortunately I have not been able to get PAM to enforce.

---

