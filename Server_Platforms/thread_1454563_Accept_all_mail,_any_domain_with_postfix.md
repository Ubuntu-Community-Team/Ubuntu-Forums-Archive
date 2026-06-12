---
title: "Accept all mail, any domain with postfix?"
date: 2010-04-14
forum: Server Platforms
---

### Post by hackajar on 2010-04-14
I am trying to setup a mail server that will accept mail from any host that attempts to send it mail, regardless of the recipient domain.

Example: 

From: [email]me@you.com[/email] To: you@<insert any domain here>

Anyone know the method for doing this in Postix?

About Request:
I have a DNS sinkhole server that is responding to redirected domains based on wild cards within my DNS server (E.g. *.dyndns.org will redirect to this server).  This is handy for web traffic, as I have a splash screen informing users that they are not allowed to access a website, but I would also like to bounce mail back to senders with a message like "your mail will not be delivered, because we restrict email to domain x".

---

### Post by KB1JWQ on 2010-04-15
DO NOT DO THIS.

A bit more info:
You must either reject in-session, or accept mail for delivery; you can't send a bounce back after the message has been received by your server.  This is caused backscatter or outscatter, and doing it can get you blacklisted in many places.

---

### Post by hackajar on 2010-04-15
Clarification:

1.) Internal Employee (user@company.com) sends email (person@badcompany.com)
2.) Internal Email server receives message
3.) Internal server does DNS MX Lookup of domain "badcompany.com"
4.) Internal server receives internal sinkhole host IP to send email to
5.) Internal mail server sends email to internal sinkhole
6.) Sinkhole receives email message
7.) Sinkhole auto-responds to sender with canned response that mail to this domain is rejected
8.) Internal mail server receives auto-reply
9.) Internal mail server forwards auto-reply message into senders mail box.

These messages would NEVER reach the Internet, and thus no backscatter should exist.

---

