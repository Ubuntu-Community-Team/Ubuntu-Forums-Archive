---
title: "Quick question about mail server config and domain"
date: 2013-03-27
forum: Server Platforms
---

### Post by zkvvoob on 2013-03-27
Hi guys,

I'm trying to set up a mail server on my Ubuntu. Just wanted to make sure about something:

I it necessary that the mail config be for ***mail***.domain.com (and therefore the domain MX records)? I want my email addresses to be [EMAIL="user@domain.com"]user@domain.com[/EMAIL], not [EMAIL="user@mail.domain.com"]user@mail.domain.com[/EMAIL].

Please advise. Thanks!

---

### Post by lisati on 2013-03-27
As I understand it, the prepending of "mail" to the recipient's domain name is more of a convention than a necessity. The important thing, as far as receiving mail is concerned, is that the sender's email provider is able to locate the recipient's provider's server.

From a DNS perspective, *one* way of organizing things is something like this:

domaina.com ---- (MX record) -----> mail.domain.com --- (A record) -----> IP address of domain.com's email server

---

