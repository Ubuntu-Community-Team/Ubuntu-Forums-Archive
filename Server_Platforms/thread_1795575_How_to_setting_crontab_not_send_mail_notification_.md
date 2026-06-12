---
title: "How to setting crontab not send mail notification to owner ?"
date: 2011-07-02
forum: Server Platforms
---

### Post by venol on 2011-07-02
Helo, How to set crontab not send mail notification to the owner script if the script success running? because I'm monitoring mail server, and notification from cron is not necessary for me. I'm using ubuntu 10.04 server
Thanks

---

### Post by Gryllida on 2011-07-02
Please try MAILTO variable solution here:

[http://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/](http://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/)

---

### Post by SeijiSensei on 2011-07-03
cron only sends mail when a program it's running creates output that isn't directed to a file.  Try something like

```

10 * * * * sh /path/to/some/script.sh >> /var/log/script.log

```

---

### Post by egpetrich on 2011-07-08
Or just send the output to /dev/null, if you have no need to save the results.

---

### Post by SeijiSensei on 2011-07-09
> **egpetrich said:**
> Or just send the output to /dev/null, if you have no need to save the results.

I originally included a pipe to /dev/null, but I decided that it was better to show people how to send the output to a log.  I didn't want to suggest to inexperienced users that it's okay to throw away potential errors without at least putting them in a log for later review.

---

