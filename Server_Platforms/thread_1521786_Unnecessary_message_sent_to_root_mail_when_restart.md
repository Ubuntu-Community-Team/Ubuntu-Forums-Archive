---
title: "Unnecessary message sent to root mail when restarting spampd daemon"
date: 2010-07-01
forum: Server Platforms
---

### Post by Yasero on 2010-07-01
Hello Everyone

I am running a mailserver with spamassassin and spampd.

Every night a cron runs that updates the spamassassin rules and restarts the spamassasssin and the spampd server.

Problem is (it is not really a problem, just something I would like to fix):

Everytime the spampd server is restartet I get the following message to the root email:
```

SUBJECT: Cron <root@hostname> /somepath/sacron

Stopping spam checking proxy daemon: spampd    ...done.
 * Starting spam checking proxy daemon spampd
   ...done.

```

This message is rather unnecessary and I would like to keep my root inbox empty for important messages.

What can I do?

Thanks so much

---

### Post by robots.jpg on 2010-07-02
If you want to stop all email from cron, you can add
```
MAILTO=""
```to /etc/crontab.

Or, assuming the spamassassin script sends errors to stderr and regular output to stdout, you should be able to add
```
 > /dev/null
```to the end of its cron entry to receive errors only.  I haven't tested this personally.

---

