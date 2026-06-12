---
title: "Mail server rejects unknown sender, but does not flush from server"
date: 2009-07-30
forum: Server Platforms
---

### Post by DaveAK on 2009-07-30
I've just set up a mail server, so I'm new at this, but here's my problem.  For one of the accounts I'm fetching mail for, there's an email that keeps getting rejected because the senders domain is not found.  This is of course a good thing, but it doesn't flush it from my ISP server, so it keeps trying to fetch it every time it polls the server.  How do I get it to reject it and flush it?

```
Jul 30 19:15:26 ubuntu-server postfix/smtpd[19649]: NOQUEUE: reject: RCPT from unknown[::1]: 450 4.1.8 <spenglerian@camaras.cantv.net>: Sender address rejected: Domain not found; from=<spenglerian@camaras.cantv.net> to=<xxx@localhost> proto=ESMTP helo=<ubuntu-server.Belkin>
Jul 30 19:15:26 ubuntu-server fetchmail[19303]: reading message xxx@yyy.com@mail.yyy.com:6 of 6 (1200 octets) (log message incomplete)
Jul 30 19:15:26 ubuntu-server fetchmail[19303]: SMTP error: 450 4.1.8 <spenglerian@camaras.cantv.net>: Sender address rejected: Domain not found 
Jul 30 19:15:26 ubuntu-server fetchmail[19303]:  not flushed
``` 

Not sure if this is a postfix or fetchmail problem.

---

### Post by DaveAK on 2009-07-30
From fetchmail manual:

> 553 (invalid sending domain)
 	Delete the message from the server. Don’t even try to send bounce-mail to the originator.

So I think this implies that postfix is sending a 450 code instead of a 553 code.  I'll see if I can figure out how to fix that.  (Hopefully.)

---

### Post by DaveAK on 2009-07-30
So here's where it gets confusing.

In /etc/postfix/main.cf I've added:

```
unknown_address_tempfail_action = reject
```

But it still doesn't reject because according to the postfix manual:

> unknown_address_reject_code (default: 450)

    The numerical Postfix SMTP server response code when a sender or recipient address is rejected by the reject_unknown_sender_domain or reject_unknown_recipient_domain restriction. The response is always 450 in case of a temporary DNS error.

    Do not change this unless you have a complete understanding of RFC 2821.

However, it doesn't differentiate between unknown recipients or unknown senders, and it warns me not to change it without a complete understanding of RFC 2821, (which of course I don't have).

Anyway, I set the reject code to 553 and it's worked, but I really don't know if that's a good thing or not.  What say the experts?

---

