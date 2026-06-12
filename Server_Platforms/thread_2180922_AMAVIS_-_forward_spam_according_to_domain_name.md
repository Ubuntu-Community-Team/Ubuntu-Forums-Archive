---
title: "AMAVIS - forward spam according to domain name"
date: 2013-10-15
forum: Server Platforms
---

### Post by Markus_Auer on 2013-10-15
Hello!

I have exactly the same problem described in [this]("http://ubuntuforums.org/showthread.php?t=928964") thread. Does anybody know if and how it is possible to configure amavis to split up spam e-mails according to domain names?

We have two MTA-Systems with postfix/ amavis/ spamassassin/ clamav which forward e-mails from the internet to different Microsoft Exchange Servers after scanning them for viruses and spam. Each MSExchange-Server handles a different set of domains, therefore I want to split up the spam to the according MSExchanges. :)

Thanks in advance!
Xylo

---

### Post by SeijiSensei on 2013-10-15
Configure postfix to deliver by domain as described here: [http://www.howtoforge.com/forums/showthread.php?t=62955](http://www.howtoforge.com/forums/showthread.php?t=62955)

---

### Post by Markus_Auer on 2013-10-15
Hi SeijiSensei!

Thank you for your response, but what is descriped in this thread is already up and running in my configuration since a few years now.

What I need to do know ist to tell amavis, that he should forward detected SPAM to specific e-mail addresses (one per domain) on the corresponding MSExchange Servers.

Spam for domain1.com should be forwarded to [EMAIL="spam@domain1.com"]spam@domain1.com[/EMAIL] on MSExchange Server 1
Spam for domain2.com should be forwarded to [EMAIL="spam@domain2.com"]spam@domain2.com[/EMAIL] on MSExchange Server 2
Spam for domain3.com should be forwarded to [EMAIL="spam@domain3.com"]spam@domain3.com[/EMAIL] on MSExchange Server 3
and so on.

If I want to simply forward all spam to an e-mail address, i can use 
$final_spam_destiny and
$spam_quarantine_to
but I have no idea, how to tell amavis to split spam based on the domain information in the recipient e-mail address.

Does anybody have an idea, how I can accomplish that?

best regards
xylo

---

### Post by SeijiSensei on 2013-10-16
You can install **procmail** as the local mail delivery agent and use "[recipes]("http://linux.die.net/man/5/procmailex")" to forward mail to another account based on characteristics of the message. However you would need to determine a method to deliver messages marked as spam to a local mailbox rather than forwarding them to the Exchange servers since procmail operates on messages as they are delivered.

I use [MailScanner]("http://www.mailscanner.info/") to filter spam.  It has the ability I describe where spams it identifies can be routed to a separate mailbox rather than delivered to the recipient.  I don't know whether your mail system can be configured to do that.

If you can figure out a way to deliver the spam locally, say to the spam@localhost account, then you could create a .procmailrc in the /home/spam directory like this:

```

:0
* ^TO.*domain1\.com
! spam@domain1.com

```

That forwards any mail arriving at this account and addressed to someone at domain1.com to the [email]spam@domain1.com[/email] mailbox.  You can add similar recipes for the other domains.

---

