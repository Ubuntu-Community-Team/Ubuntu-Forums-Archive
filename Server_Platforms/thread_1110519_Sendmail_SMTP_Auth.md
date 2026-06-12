---
title: "Sendmail SMTP Auth"
date: 2009-03-29
forum: Server Platforms
---

### Post by allinurl on 2009-03-29
Hi everybody, I did setup SMTP auth on sendmail.

My problem is, if I configure my outgoing server on my **mail client** as mail.domain.com _without_ enabling "My SMTP server requires auth" I'm, still able to send emails.

I'm not quite sure what I'm missing.

telnet mail.domain.com 25

EHLO yahoo.com
250-hostname.isp.com Hello mail.domain.com [100.100.100.100], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH LOGIN PLAIN DIGEST-MD5 CRAM-MD5
250-STARTTLS
250-DELIVERBY
250 HELP

Any clues? thanks

---

### Post by dessss on 2009-04-02
Hi,

what is in your /etc/mail/sasl/Sendmail.conf.2 file?

---

