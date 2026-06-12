---
title: "Postfix accepting mails from specific domains"
date: 2007-05-31
forum: Server Platforms
---

### Post by yepezrendon on 2007-05-31
Hi,

I don't know if what I'm trying to do is possible, but here is my scenario:


 local.domain (LAN)
       |
       |  Send and receive mails from and to local.domain
       |  Send and receive mails from and to example.com
       |
Postfix Server
       |
       | Accept mails only from example.com
       | Reject from 
       |
Internet

I already can send and receive mail in my local area network within my local domain (which is a full qualified domain name).
If I send mail to an external domain, Postfix rejects mail.
If I send mail from my external domain to local.domain, Postfix rejects mail

I only want to open communication with example.com and reject anything else (i.e. hotmail, yahoo, etc).

This is my my.cnf file:

myhostname = odiseo.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = odiseo.example.com, localhost.example.com, , localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

I know it must be simple to solve this issue, but I can't get how to do it.

Many thanks in advance,
Gabriel

---

