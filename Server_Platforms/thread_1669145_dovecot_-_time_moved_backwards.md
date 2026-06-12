---
title: "dovecot - time moved backwards"
date: 2011-01-17
forum: Server Platforms
---

### Post by guest_user on 2011-01-17
dovecot is setup to run on each startup but each time I restart my system, I find that it is not running(killed), when I check my logs it says time moved backwards for x seconds. Essentially, I'm having this problem,
[http://wiki.dovecot.org/TimeMovedBackwards](http://wiki.dovecot.org/TimeMovedBackwards)

what is the solution in ubuntu so that dovecot would not be killed on startup?

currently I have to put /etc/init.d/dovecot restart into rc.local to restart it again...

---

### Post by SeijiSensei on 2011-01-17
Well, are you running ntpdate to synchronize your clock like that Wiki article mentions?  If so, run ntpd instead as the article suggests.  Install it with "sudo apt-get install ntp".  Then edit (as root) the file ntp.conf to add a few time servers from the [pool.ntp.org]("http://www.pool.ntp.org/") project.

If you're not synchronizing your clock at all, that's a bad idea for a mail server where times are critical.  PC hardware clocks aren't especially accurate.  Use ntpd, and you should not see this problem again.

---

