---
title: "mail host set up"
date: 2011-12-05
forum: Server Platforms
---

### Post by zensys on 2011-12-05
I just installed Ubuntu Server (10.04) with Postfix and Dovecot for my newly acquired VPS with one IP-address. I can now send mail from the command line and receive mail (with mail command). But now I need to configure my email client and run into a few basic questions on best practice:

1. During install I chose 'myhost' as my machine name so myhostname is 'myhost.mydomain.com' But I would like to use 'mail.mydomain.com' as my smtp and pop servers (I like conventions). Is that possible or should I use myhost.mydomain.com? If possible how should I configure 
main.cf?

2. Apart from root I have one user ('first'). If I want to use as 
email addresses 'i...@mydomain.com' and first.l...@mydomain.com', 
should I add these as users to myhost or are there better/easier ways? If I do add users, will they be users for 'myhost' or for 'mail' (or both)?

I have set up the following DNS records with my hosting provider: 
A: myhost.mydomain.com 12.34.567.89 
A: mail.mydomain.com 12.34.567.89 
A: *.mydomain.com 12.34.567.89 
A: mydomain.com 12.34.567.89 
MX10: mydomain.com mail.mydomain.com 
MX20: mydomain.com fallback.mail.hostingprovider.com

I want to add more domains to the same IP address. I know there are ways to add virtual mail boxes but I want to take things one step at a time. I just mention this for if it would influence the set up of the main domain.

---

