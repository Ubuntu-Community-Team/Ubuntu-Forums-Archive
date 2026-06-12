---
title: "Lost incoming email and web server!"
date: 2010-06-28
forum: Server Platforms
---

### Post by ckuecker on 2010-06-28
Somehow, I have broken my email receive and my web server. Postfix, dovecot, and apache2 are all running. I can send emails. If I try to access the web server via the local server's IP, I can see my webpages. If I try to fetch emails, I get "connection refused", and if I try to access the web pages via the URL, I get a "can't connect" error.

I run my own bind9 DNS server - it's been working fine for over a year. The only two things thing I can think of that could have done this are an aborted attempt to install tinydns / djbdns in place of bind9 - I never finished the install, and djbdns is not running, and second, the addition of one line to my DNS zone file to steer traffic to another computer on my network. I've commented out that line and completely removed djbdns for now.

Anyone have an idea where to look to fix this?

---

### Post by ckuecker on 2010-06-29
Never mind - it was my router firewall. I was trying to allow outside access to anotehr computer on my network, and inadvertently broke it.

All better.

---

