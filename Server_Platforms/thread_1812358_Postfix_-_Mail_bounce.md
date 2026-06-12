---
title: "Postfix - Mail bounce"
date: 2011-07-26
forum: Server Platforms
---

### Post by russel_sc on 2011-07-26
Hi All.

It's highly appreciated if someone can tell me a solution for my below problem: - 


I have a postfix mail server on ubuntu 10.04 lts behind a router. so all local users are fetching/sending mails through ms outlook using local IP. Sometimes when internet goes down and any mail send then it bounced back immediately saying domain not found. Can u please tell me how i configure to hold all mails in postfix server rather than bounce when internet fails and will pass through when restored the internet around 15-30 minutes?

Thank u.


Regards,
Russel.

---

### Post by mlentink on 2011-07-26
You mean it bounces local mail? Is your local domain parameter set in the config files?

---

### Post by russel_sc on 2011-07-26
No, not the local mails but outside recipient's mail.

---

