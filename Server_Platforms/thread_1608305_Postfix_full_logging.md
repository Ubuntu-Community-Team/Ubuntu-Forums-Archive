---
title: "Postfix full logging"
date: 2010-10-28
forum: Server Platforms
---

### Post by mmxbass on 2010-10-28
I have a postfix+courier setup for an organization and we're currently looking into employee accountability. Specifically I'm looking for information on how to configure postfix to, ideally, keep a 2nd inbox/outbox (or at least some kind of record) of every e-mail that is sent to or from certain user accounts.

Obviously certain users should also be not logged.

Any thoughts?

 - JP

---

### Post by SeijiSensei on 2010-10-28
/var/log/mail.log should already include the sender and recipient address of every message Postfix handles.

On the delivery side, you can install procmail and add a .procmailrc to the accounts you wish to monitor.  A simple rule like this in /home/user/.procmailrc:

```

:0c
! hall_monitor@example.com

```

sends a copy of every message delivered to the user to the hall_monitor address.  See "man procmailrc" and "man procmailex" for details.

I can't really answer on the outbound side since I don't use Postfix.  I do run [MailScanner]("http://www.mailscanner.info/") (with sendmail) which has the ability to send a copy of every message it processes in either direction to a specified address.  I suspect you can use it to monitor particular accounts as well using the MailScanner ruleset functions. MailScanner is in the repositories if you'd like to take a look.

---

### Post by mmxbass on 2010-10-30
I'll take a look at this and let you know how it turns out.

---

