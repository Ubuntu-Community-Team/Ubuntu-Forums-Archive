---
title: "Mailman with postfix on 6.06"
date: 2008-01-15
forum: Server Platforms
---

### Post by larsemil on 2008-01-15
i followed this guide: 
[https://help.ubuntu.com/community/Mailman](https://help.ubuntu.com/community/Mailman)

to install mailman. And everything is fine and working good until i am trying to send a email TO a list. What i get then is this error:
```
Reporting-MTA: dns;intrapost.avhold.no
Received-From-MTA: dns;[192.168.0.129]
Arrival-Date: Tue, 15 Jan 2008 14:08:20 +0100

Final-Recipient: rfc822;test@lister.juvente.no
Action: failed
Status: 5.7.1
Diagnostic-Code: smtp;554 5.7.1 <test@lister.juvente.no>: Recipient address rejected: Access denied

```

on the serverside i get this: 
```

Jan 15 15:00:39 leon postfix/smtpd[11852]: warning: 194.14.10.10: hostname mail2.nbv.se verification failed: Name or service not known
Jan 15 15:00:39 leon postfix/smtpd[11852]: connect from unknown[194.14.10.10]
Jan 15 15:00:39 leon postfix/smtpd[11852]: NOQUEUE: reject: RCPT from unknown[194.14.10.10]: 554 5.7.1 <test@lister.juvente.no>: Recipient address rejected: Access denied; from=<X@unf.se> to=<test@lister.juvente.no> proto=ESMTP helo=<sobex01.sobernet.net>
Jan 15 15:00:39 leon postfix/smtpd[11852]: warning: restriction `_unauth_destination' after `reject' is ignored
Jan 15 15:00:39 leon postfix/smtpd[11852]: disconnect from unknown[194.14.10.10]



```

i have no clue what to do.. as the server actually recieves the email and then rejects it makes me believe there is something wrong between mailman and postfix.. 

Anyone have any ideas?

---

### Post by larsemil on 2008-01-15
none?

---

### Post by MJN on 2008-01-15
I've not used Mailman so can only really help with the Postfix side of things.

Your Postfix config is certainly broken (possibly a space between **reject** and **_unuth_destination**) but I wouldn't have thought this is the complete fault.

Aside from the mailman aspects does your Postfix service run okay (accepting messages particularly)?

Mathew

---

### Post by larsemil on 2008-01-16
> **MJN said:**
> 
Your Postfix config is certainly broken (possibly a space between **reject** and **_unuth_destination**) but I wouldn't have thought this is the complete fault.


well that actually solved the problem! thanks alot!:KS

---

### Post by MJN on 2008-01-16
Damn... should've been more confident! ;)

---

### Post by larsemil on 2008-01-16
it was up and working for a while, and then all the sudden: 
```

Jan 16 16:30:46 leon postfix/smtpd[32223]: warning: 194.14.10.10: hostname mail2.scout.se verification failed: Name or service not known
Jan 16 16:30:46 leon postfix/smtpd[32223]: connect from unknown[194.14.10.10]
Jan 16 16:30:46 leon postfix/smtpd[32223]: NOQUEUE: reject: RCPT from unknown[194.14.10.10]: 550 5.1.1 <test@lister.juvente.no>: Recipient address rejected: User unknown in local recipient table; from=<emil@unf.se> to=<test@lister.juvente.no> proto=ESMTP helo=<sobex01.sobernet.net>
Jan 16 16:30:46 leon postfix/smtpd[32223]: disconnect from unknown[194.14.10.10]

```

I have no idea why? anyone?

looks like mailman is not taking over the delivery anymore...

---

