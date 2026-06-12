---
title: "postfix/dovecot mail loop back itself !?"
date: 2012-04-20
forum: Server Platforms
---

### Post by dchen on 2012-04-20
Test mail server: Ubuntu server 11.10 configured with postfix/dovecot/squirrelmail, ...
                           hostname: testmail.example.com has its own MX record separate from the parent 
                           domain (example.com)'s MX record.

The production server: Fedora 11, also configured with postfix/dovecot/squirrelmai,...
                           hostname: example.com

Tried to send a mail from an account in the testmail.example.com domain, i.e. [email]john@testmail.example.com[/email],  to an account in the example.com domain, i.e. [email]dave@example.com[/email], the result: [email]dave@example.com[/email] DO NOT receive the mail, instead [email]dave@testmail.example.com[/email] gets the mail.

From the mail.log in testmail.example.com, it seemed that it relayed to local itself, it did not go thru the example.com host.

Where are places in postfix configuration in testmail.example.com server or some where that can be set up to send mails from submain to parent domain successfully and vice versa ?  thx

---

### Post by smtp on 2012-04-23
Check **mydestination **configuration parameter in Postfix (main.cf) and adopt it accordingly (that on testmail.example.com).

---

### Post by dchen on 2012-04-24
> **smtp said:**
> Check **mydestination **configuration parameter in Postfix (main.cf) and adopt it accordingly (that on testmail.example.com).
I have the mydestination = testmail.example.com, example.com, localhost.example.com, localhost
in the main.cf of testmail.example.com, is this right ?

---

