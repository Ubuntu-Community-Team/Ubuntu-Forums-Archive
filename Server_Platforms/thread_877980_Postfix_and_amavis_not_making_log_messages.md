---
title: "Postfix and amavis not making log messages"
date: 2008-08-02
forum: Server Platforms
---

### Post by mootpoint on 2008-08-02
I did an oops a few days ago, and wiped out /sbin on my email server. I replaced it with /sbin from another box. Ever since, postfix and amavis are working fine, filtering, delivering email, etc., but neither one is logging to /var/log/mail.log (or anywhere else I can find). Additional information:

1) The logging daemon itself seems fine. 
2) postgrey and imapd processes are logging messages to /var/log/mail.log just fine. 
3) I tried taking postfix out of chroot in master.cf and restarting, no change.

Any ideas? It's hard to troubleshoot when there are no log messages!

m00t

---

### Post by mootpoint on 2008-08-03
Fixed it. The /dev/log device was also gone. /etc/init.d/sysklogd restart recreated the device, and now all is well.

m00t

---

