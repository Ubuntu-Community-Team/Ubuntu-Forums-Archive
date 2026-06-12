---
title: "Postfix warning"
date: 2010-10-24
forum: Server Platforms
---

### Post by lisati on 2010-10-24
I'm having a "What the....?" moment here. I just noticed that on my system postfix had issued this warning a handful of times:
> warning: /var/spool/postfix/lib/libnss_nisplus-2.10.1.so and /lib/libnss_nisplus-2.10.1.so differ
Google yielded no information. After rebooting it seems to have gone away.

I'm running Ubuntu 9.10 server edition, and Postfix version 2.6.5.

Any ideas on what it means beyond the obvious?

---

### Post by kidders on 2010-10-25
Hi there,

That looks like something to do with postfix's chroot jail. I'm not running postfix at the moment, so I can't test this out for you, but my first guess would be that the jail got out of sync with the rest of your system somehow.

Did you by any chance upgrade /lib/libnss_nisplus-2.10.1.so since you'd last restarted postfix? Rebooting will have had the same effect as running **/etc/init.d/postfix restart**, which presumably re-synced the chroot jail & corrected the inconsistency.

Assuming I'm right (a big leap!), I can't help wondering if the maintainers of packages like libc6 ought to have been able to foresee this issue & have their post-install scripts restart chrooted postfix servers. If you think so, it might be worth filing a bug ... In theory, using two different libnss-related libraries at once could create name resolution problems & cause mail to bounce.

Sorry I can't be more definitive ... I hope that's of *some* help.

---

### Post by lisati on 2010-10-25
Thanks for the response, and sorry about the delay responding. I'm at work at the moment, and if I remember I'll have a closer look when I get home.

---

### Post by lisati on 2010-10-31
Marked as "Solved": seems to have been a one-off problem.

---

