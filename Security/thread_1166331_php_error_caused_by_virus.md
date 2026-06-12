---
title: "php error caused by virus?"
date: 2009-05-21
forum: Security
---

### Post by fallen seraph on 2009-05-21
I was visiting a website that I regularly read this morning and I got this message: > 
Warning: session_start() [function.session-start]: open(/tmp/sess_e6c9f022e9eaa9aabb1f815d9479a7e0, O_RDWR) failed: Permission denied (13) in /home/etf2l/etf2l.org/htdocs/wp-content/plugins/wordpress-automatic-upgrade/wordpress-automatic-upgrade.php on line 121

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /home/etf2l/etf2l.org/htdocs/wp-content/plugins/wordpress-automatic-upgrade/wordpress-automatic-upgrade.php:121) in /home/etf2l/etf2l.org/htdocs/wp-content/plugins/wordpress-automatic-upgrade/wordpress-automatic-upgrade.php on line 121


Could this be caused by a virus trying to do something to the pages that I look at?

This does not appear when the webpage is accessed on another OS or computer.

I ask because I recently got banned from another website for a while, and the reason given was 'running a virus', and I've no idea what this is in reference to, so I had attributed it to dynamic ips...

---

### Post by The Tronyx on 2009-05-21
```

Warning: session_start() [function.session-start]: open(/tmp/sess_e6c9f022e9eaa9aabb1f815d9479a7e0, O_RDWR) failed: Permission denied (13) in /home/etf2l/etf2l.org/htdocs/wp-content/plugins/wordpress-automatic-upgrade/wordpress-automatic-upgrade.php on line 121

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /home/etf2l/etf2l.org/htdocs/wp-content/plugins/wordpress-automatic-upgrade/wordpress-automatic-upgrade.php:121) in /home/etf2l/etf2l.org/htdocs/wp-content/plugins/wordpress-automatic-upgrade/wordpress-automatic-upgrade.php on line 121

```

This is a server side error.

---

