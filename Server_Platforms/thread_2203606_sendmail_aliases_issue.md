---
title: "sendmail aliases issue"
date: 2014-02-04
forum: Server Platforms
---

### Post by laurent_Debacker on 2014-02-04
Hi,
On a Linux server, I would like to re-route crontab mails to an external e-mail server, using sendmail.
I am using the aliases files for this, which works fine.

However, the aliases don't replace the TO header inside the message. Only the envelope destination is replaced.
So, when receiving the message on my e-mail client (Outlook, actually), I see it as intended to [EMAIL="root@themachine.thedomain"]root@themachine.thedomain[/EMAIL] instead of intended to me.

How is it possible to change this behaviour?

Thanks for the help.

Laurent.

---

### Post by SeijiSensei on 2014-02-04
You can add a MAILTO variable to the top of the crontab with your address as the destination.  For instance, in /var/spool/cron/root you would have 
```

MAILTO=me@example.com

[etc.]

```
Now root's crontab mail will be sent to that address rather than via forwarding by aliasing.

---

