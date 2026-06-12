---
title: "Can't root receive any email with postfix ?"
date: 2015-08-19
forum: Server Platforms
---

### Post by luofeiyu2011 on 2015-08-19
There are two users : root and ubun in my system.
The domain name is pengsir.hfi

I fount that root can't receive any email sent to it.

    ehco 'test' | mail -s 'test' root@localhost
    su root
    mail
    No mail for root
    cat /var/log/mail.log

Aug 19 15:47:49 pengsir postfix/pickup[3769]: 9F84FF829F: uid=1000 from=<ubun>
Aug 19 15:47:49 pengsir postfix/cleanup[3808]: 9F84FF829F: message-id=20150819074749.9F84FF829F@pengsir.hfi
Aug 19 15:47:49 pengsir postfix/qmgr[3770]: 9F84FF829F: from=ubun@pengsir.hfi, size=287, nrcpt=1 (queue active)
Aug 19 15:47:49 pengsir postfix/local[3810]: 9F84FF829F: to=root@pengsir.hfi, orig_to=root@localhost, relay=local, delay=0.24, delays=0.14/0.01/0/0.1, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Aug 19 15:47:49 pengsir postfix/qmgr[3770]: 9F84FF829F: removed

Why the email was removed?

---

### Post by lisati on 2015-08-19
The "removed" in this context likely refers to being removed from the delivery queue. The mail should now be in your mailbox.

---

### Post by SeijiSensei on 2015-08-19
> **lisati said:**
> The mail should now be in your mailbox.
Specifically, in /var/mail/root.

I notice you're using procmail as the delivery agent.  If you have specified any "recipes" for root's mail, then it will be handled according to your recipes.

---

