---
title: "unstoppable smtp relay"
date: 2007-06-09
forum: Server Platforms
---

### Post by lvanderree on 2007-06-09
Hello, 

I think someone is trying to use my machine as a smtp relay server, but I can't find a way to stop him.

I keep getting these messages in my log-file, and until now he didn't succeed in sending mail through my machine, but I think it is quiet annoying.

```

Jun  9 10:58:01 fun4me postfix/smtpd[2734]: warning: 122.116.16.145: hostname 122-116-16-145.HINET-IP.hinet.net verification failed: No address associated w
ith hostname
Jun  9 10:58:01 fun4me postfix/smtpd[2734]: connect from unknown[122.116.16.145]
Jun  9 10:58:02 fun4me postfix/smtpd[2734]: NOQUEUE: reject: RCPT from unknown[122.116.16.145]: 554 5.7.1 <kikiuki88a@yahoo.com.tw>: Relay access denied; fr
om=<b52.b52@msa.hinet.net> to=<kikiuki88a@yahoo.com.tw> proto=SMTP helo=<83.160.225.5>
Jun  9 10:58:03 fun4me postfix/smtpd[2734]: lost connection after RCPT from unknown[122.116.16.145]
Jun  9 10:58:03 fun4me postfix/smtpd[2734]: disconnect from unknown[122.116.16.145]

```

I added his IP to /etc/hosts.deny but I still keep getting these messages, can someone explain me why this is possible and how to stop this.

Thanks in advance

---

### Post by MJN on 2007-06-09
It's likely to be futile blocking by IP address as the spammer will probably be moving onto to his next IP from which to send mails out hence you'll always be playing catch-up.

Your mail server is doing it's job - not acting as an open relay - so I suggest just leaving it be. You mustn't let log entries 'annoy' you - indeed they're merely telling you everything is fine and dandy which should be taken a good thing!

In answer to your question, Postfix doesn't use TCP Wrappers (trivia side note: Postfix and TCP Wrappers were actually created by the same person) hence /etc/hosts.deny will have no effect - besides which what's the difference between Postfix stopping access, as now, or TCP Wrappers? The absence of such a note in a logfile...?

Notwithstanding the above, if you really want to filter on client IP address then use Postfix itself with the **smtpd_client_restrictions** directive (see [http://www.postfix.org/postconf.5.html#smtpd_client_restrictions](http://www.postfix.org/postconf.5.html#smtpd_client_restrictions)) and, in particular, the **check_client_access type:table** option.

Finally, for what it's worth, you're not being 'singled out' here by the spammer - what you're seeing is all quite normal for probably every mail server out there...

Mathew

---

### Post by lvanderree on 2007-06-09
Thanks for your answer.

I didn't new about Postfix and TCP Wrappers, but this explains. I was already wondering if maybe I wasn't initiating the relay request in some strange way. But I wanted to stop this because I don't like these attacks and this one caught my attention because logcheck mentioned it for a non-matching dns result.

Now I have changed the log-check file so it doesn't botter me anymore, because as you already said, It will continue happening by others as well, which won't be noticed because their IP and reverse DNS lookup will match.

I guess I can also install a firewall to solve this issue (I'm now behind a router with NAT) but I think I leave it this way for now.

again, thanks for the info.

---

### Post by Mr. C. on 2007-06-09
Unless the attack is lengthy and persistent, there is no need to reject via tcpwrappers or a firewall. Postfix does its job just fine.

MrC

---

