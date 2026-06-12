---
title: "Rejecting backscatter with Postfix"
date: 2015-05-07
forum: Server Platforms
---

### Post by FuturePilot on 2015-05-07
I've recently been getting a lot of [backscatter]("http://en.wikipedia.org/wiki/Backscatter_%28email%29") on my email server. How can I make Postfix reject emails to a non-existent user on my server instead of sending back a bounce message??

---

### Post by SeijiSensei on 2015-05-08
In principle you can't, because the [SMTP protocol specifications]("https://www.ietf.org/rfc/rfc2821.txt") require a non-deliverable notice be sent.
> The second step in the procedure is the RCPT command.

      RCPT TO:<forward-path> [ SP <rcpt-parameters> ] <CRLF>

   The first or only argument to this command includes a forward-path
   (normally a mailbox and domain, always surrounded by "<" and ">"
   brackets) identifying one recipient.  If accepted, the SMTP server
   returns a 250 OK reply and stores the forward-path.  [B]If the recipient
   is known not to be a deliverable address, the SMTP server returns a
   550 reply[/B], typically with a string such as "no such user - " and the
   mailbox name (other circumstances and reply codes are possible).

My outbound mail queues often have some number of non-deliverable notices that cannot be delivered to the bogus sender addresses used by spammers.  Eventually the NDNs expire.  I stopped worrying about problems like these some time ago.

What are you using for spam filtering?  If the message gets quarantined or deleted by the spam filter before delivery, it won't generate nondeliverable notices.

---

### Post by Lloyd_mcse on 2015-05-09
What about...

```

## Restrictions
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, **reject_unauth_destination**
smtpd_client_restrictions = permit_mynetworks, permit_sasl_authenticated, **reject_rbl_client b.barracudacentral.org, reject_rbl_client sbl.spamhaus.org, reject_rbl_client zen.spamhaus.org**
```

Along with Spamassasin.
I hope it helps
Kind regards

Lloyd

---

### Post by SeijiSensei on 2015-05-09
I use these in main.cf:
```

smtpd_client_restrictions = reject_unknown_client_hostname, sleep 3, reject_unauth_pipelining
smtpd_sender_restrictions = reject_unknown_sender_domain

```
Reject_unknown_client_hostname is the most effective, but also the most stringent.  It blocks connections from any machine that does not have proper DNS resolution.  Nearly every legitimate mail server has correct forward and reverse resolution configured these days, so the likelihood of false positives is still pretty low.

The "sleep3, reject_unauth_pipelining" pair tell the server to wait three seconds after the client connects before displaying its "banner" in the SMTP exchange.  Though their numbers are declining, some spam programs don't wait for the banner and start spewing right away.  "Reject_unauth_pipelining" tells Postfix to hang up the phone of any such clients.

"Reject_unknown_sender_domain" applies to the email address sent with the "MAIL FROM" command in the SMTP dialogue (known as the "envelope sender"). That rule requires the email address be @ a valid domain.  Non-deliverable notices are sent to that address so it could have some, though I suspect small, effect of reducing NDNs to bogus addressees.  Note that the sending server isn't asked to validate that the message comes from a workign address (since it often can't); the only check is whether the sender's domain exists.

You should also browse the possibilities in: [http://www.postfix.org/ADDRESS_VERIFICATION_README.html](http://www.postfix.org/ADDRESS_VERIFICATION_README.html)

---

### Post by FuturePilot on 2015-05-09
So my problem ended up being a misconfiguration. Even though I changed 
```
-o smtpd_reject_unlisted_recipient=yes
```
in master.cf it wasn't working then I realized I had 
```
virtual_mailbox_maps = hash:/etc/postfix/virtual_mailbox_maps
```
commented out in main.cf. #-o

Found this that helped. A lot of the other things I've read don't work anymore with recent versions of Postfix
[http://wiki2.dovecot.org/LDA/Postfix]("http://wiki2.dovecot.org/LDA/Postfix")

Now it gives a 550 for unlisted addresses in virtual_mailbox_maps.

---

