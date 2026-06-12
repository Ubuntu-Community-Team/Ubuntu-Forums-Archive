---
title: "Send only mail server with multiple domains"
date: 2014-01-25
forum: Server Platforms
---

### Post by sunilkjoseph on 2014-01-25
I am not an expert on Ubuntu, but I did manage to move a few personal blogs from my shared hosting to a VPS. These are low volume sites and I do have daily backups, so I am not worried about experimenting. I was able to get everything running as I want, except for email and I hope people over here will be able to give me some guidance.

[LIST]
[*]Need only MTA to send system mails, registration, IP ban, comment notification. Incoming mail is never checked and is hosted on Google apps.
[*]Email has to go from respective domains.
[/LIST]

After playing around with postfix, I was able to send mail from my primary domain, but not with the other 2 which are hosted. I suspect either 1 or more of the below reasons to be the problem.

[LIST=1]
[*]The first domain has vps.example1.com pointing towards the server IP, the other 2 doesn't.
[*]Destination domains in postfix configuration. Should it contain all domains from where I need to send email? "Destination" is confusing.
[*]Should Hosts file contain loopback ip for each domain?
[/LIST]

I would have tried each of these steps on the VPS, but I got the rest of the things running smoothly (page load is less than 1 sec on all sites) and I would prefer to understand this better before I try any more experimentation. Thanks in advance.

---

