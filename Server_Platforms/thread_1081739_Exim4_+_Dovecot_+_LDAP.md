---
title: "Exim4 + Dovecot + LDAP"
date: 2009-02-26
forum: Server Platforms
---

### Post by constchar* on 2009-02-26
Hello fellow Ubuntu'ers.
I need some help in the right direction with my latest task.

I have to setup a complete mail server on Ubuntu 8.10 and after
some research I decided to use Exim4 and Dovecot.

Dovecot was real easy to setup and their documentation is straightforward and really helpful without having to flip through pages and pages of blinding text.
Exim on the other hand proves to be a real pain, and its documentation is quite lengthy.

Basically what I need to do is setup POP3, IMAP and SMTP servers
that use LDAP as a backend for authentication and users.

Dovecot worked like a dream and I was able to set it up with LDAP with no problems at all, and as a bonus I was able to setup Exim to authenticate via Dovecot's SASL.

The problem is however is that I am able to send mail using any
user I desire from the LDAP however when I try to receive mail I get a "Unroutable address" message bounced back.
This understandable as after some research I discovered that Exim only receives mails to local users.

How can I get Exim to deliver mail to LDAP-based users?

Also as a side question how do I get Exim to send mail for any authenticated user without getting a "Relay not permitted message" (otherwise I have to add "0.0.0.0/0" as a permitted relay machine, which is really bad)?

Thanks for any help.

---

