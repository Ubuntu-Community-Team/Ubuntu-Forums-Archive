---
title: "Getmail - username with special character"
date: 2011-11-14
forum: Server Platforms
---

### Post by kamaji792 on 2011-11-14
I am trying to set up **Getmail** to retrieve emails from a server.  Unfortunately my ISP creates individual e-mail boxes based on the main user (smiths) and box name (john), so:
```
smith+john
```

When I setup Getmail rc file for john like:
```
[retriever]
type = SimplePOP3Retriever
server = mail.plus.net
username = smiths+john
password = aBetterPassword

[destination]
type = Maildir
path = /var/mail/john@smiths.com/Maildir/

[options]
delete = false
read_all = false

```

Getmail creates a mail box for **smiths**.

Anyone know if there is a way to get round this problem? k

---

### Post by Wayne_V on 2011-11-14
have you tried "smiths+john" or smiths\+john ?

---

### Post by kamaji792 on 2011-11-14
I think I have solved my problem.

Just a little bit of background.  I am using **Getmail** to feed a **Dovecote** mail server.  Effectively doing a POP3 to IMAP conversion.

I was following this how-to [https://help.ubuntu.com/community/POP3Aggregator]("https://help.ubuntu.com/community/POP3Aggregator")

It was not **Getmail** that was creating the mail box it was **Dovecote**.

This is the first time I have done anything like this and I am still coming to grips with it.

What my rc file should have looked like was:
```
[retriever]
type = SimplePOP3Retriever
server = mail.plus.net
username = smiths+john
password = aBetterPassword

[destination]
type = Maildir
path = /var/mail/smiths/Maildir/

[options]
delete = false
read_all = false
```
The only line that changes is **path = /var/mail/smiths/Maildir/**.

I believe Dovecote has a problem with account names that are not URL friendly (though + => %2B may work).

---

### Post by Jonathan L on 2011-11-14
Hi Kamaji

> ...Unfortunately my ISP creates individual e-mail boxes based on the main user (smiths) and box name (john), so:
```
smith+john
```...Just in passing you might note that '+' is a very common for subaddressing, where user+thing@domain gets delivered to user@domain.  Google's gmail, for example, uses '+' for this, and it's a very useful though not widely-known part of email addressing.  The part to the left of '@' is considered local to the receiving system, and it's allowed to do surprising things with it.  Subaddressing is formalised in [RFC 5233]("http://tools.ietf.org/html/rfc5233"), while addresses in general are covered in [RFC 5322.]("http://tools.ietf.org/html/rfc5322")

Hope that's some interest!

Kind regards,
Jonathan.

---

