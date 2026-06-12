---
title: "Setup postfix mail server and courier-imap/pop."
date: 2010-02-23
forum: Server Platforms
---

### Post by blueocean89 on 2010-02-23
Hi guys, I need your help to setup my postfix mail server and courier-imap/pop.

My postfix server now is working with tls and saslauthd, I can send/receive email inside my domain as well as outside. However, I need two separate smtp and imap/pop3 server, I mean two machine - one with smtp function and one with imap/pop3 function working together. I haven't find out solution for this case, even the keyword to do some googling. Are there any people who can give me some instructions?

Thanks in advanced ! And sorry for my poor english [ I'm trying to improve it].

---

### Post by blueocean89 on 2010-02-23
anyone can help me?, please

---

### Post by noway2 on 2010-02-24
If you really want or must run the SMTP and POP/IMAP on separate machines you have some complex configuration issues that go beyond they typical.  Are you certain that this is the best solution to your problem?

To do this, you will need to find a way to co-ordinate the two machines.  The SMTP needs to know where to store the mail and the POP/IMAP needs to know where to get it.  Both need to be able to access this location.

---

### Post by blueocean89 on 2010-02-25
hi noway2,
thank you very much for your reply,

So, as you said,all I have to deal with now is the mailbox and email storage? What if I setup a mailbox on pop/imap machine then share it (for example, through NFS) for smtp to put emails on that NFS share? Is it the right method? Is there anything esle I have to do? My email system use NIS domain account.

---

### Post by noway2 on 2010-02-26
That is what I would attempt, yes.  Have your MTA store the mail in a location that is accessible as a network share.  Then configure dovecot to read from that location.  Once the drives are mounted and accessible, it shouldn't matter logically whether or not they are on the same system or shared.

---

