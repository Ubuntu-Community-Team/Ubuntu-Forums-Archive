---
title: "mail"
date: 2006-09-16
forum: Server Platforms
---

### Post by Compact on 2006-09-16
Every day I receive some mails from the crontab. Is it posible to send this messages to my normal mail and erase they from the server?

---

### Post by chrisfay on 2006-09-16
If you don't want them at all just add this to the end of the crontab line:

> /dev/null 2>&1

---

### Post by lamego on 2006-09-17
This feature was from sendmail I guess it should work with postfix.
You will need to create a .forward file on your home dir with the email you want to forward the emails to.

You can read about it here:
[http://www.feep.net/sendmail/tutorial/intro/forward.html](http://www.feep.net/sendmail/tutorial/intro/forward.html)

---

