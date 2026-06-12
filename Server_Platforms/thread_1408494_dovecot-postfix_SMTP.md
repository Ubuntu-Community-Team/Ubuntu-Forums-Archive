---
title: "dovecot-postfix SMTP"
date: 2010-02-16
forum: Server Platforms
---

### Post by japsai on 2010-02-16
Hi,

Following the [server guide]("https://help.ubuntu.com/8.04/serverguide/C/postfix.html") to the letter, i tried to install mail serving capabilities on my ubuntu 9.04 virtual server hosted at STRATO.

I installed dovecot-postfix, created certificates and changed the certificate references, as in the guide. Sending and receiving email works, as well as IMAP external email downloading over SSL. However SMTP doesn't work.

When testing with "telnet mydomain.com 25" and "ehlo mydomain.com" I do not have the lines

```

250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN

```

as in the guide. Is this the problem? If so, what should I change?

---

### Post by japsai on 2010-02-17
Is it possible to file a ticket against the serverguide somewhere?

---

### Post by Syl21 on 2011-08-18
Hello,

I've the same problem...

I can connect localy but not from anywhere...

Have you found the solution???

Thx in Adv

---

### Post by japsai on 2011-08-18
No I didn't. I found the dovecot-postfix configuration too complicated for my purpose, and am now using a free Google Apps account, only had to change my MX record.

---

### Post by rudelgurke on 2011-08-19
> **Syl21 said:**
> Hello,

I've the same problem...

I can connect localy but not from anywhere...

Have you found the solution???

Thx in Adv

Please post the output of "postconf -n" - thank you. Specially interesting are:

inet_interfaces / mynetworks

If you didn't changed things in the "master.cf" file manually.

---

