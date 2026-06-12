---
title: "Command Line Email?"
date: 2008-11-09
forum: Server Platforms
---

### Post by tofuconfetti on 2008-11-09
Before I make a mistake on this one, can anyone just tell me what they feel is the easiest way to get command line email working for a cron task?  I want the lightest weight, easiest to configure way if possible.

Thanks.

---

### Post by koenn on 2008-11-09
mail

The program 'mail' can be found in the following packages:
 * mailx
 * mailutils

---

### Post by CrucifiedEgo on 2008-11-09
```
apt-get install mailx

echo "mail contents" | mail -s "Mail subject" user@domain.com
```

You can pipe the output of anything to mail... example, df -h | mail -s "Disk Usage" [email]me@example.com[/email] could be cronned to send you a mail report dailiy (though that's not the best way to do it, it's an efficient example.)

---

