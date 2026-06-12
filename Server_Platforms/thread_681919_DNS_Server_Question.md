---
title: "DNS Server Question"
date: 2008-01-29
forum: Server Platforms
---

### Post by alt4max on 2008-01-29
Hi guys, have a question about DNS Server. I am in transition to move my website from shared to dedicated host and right now I figured out how to configure apache, php, mysql (website working fine). I'll use this server only for this website so do I need DNS Server or I can just point domain name register to IP address? If so what will be the best practice?

Thx. in advance.
Alt

---

### Post by HermanAB on 2008-01-29
If your registrar has a DNS service, use it.  You are paying for it already.

Cheers,

Herman

---

### Post by alt4max on 2008-01-29
Thx. HermanAB for reply, also I need to install/configure mail server as well, what do you suggest will be the best and easy to use.

Thx. in advance.
Alt

---

### Post by koenn on 2008-01-29
> **alt4max said:**
> Thx. HermanAB for reply, also I need to install/configure mail server as well, what do you suggest will be the best and easy to use.

Thx. in advance.
Alt
He's gonna say 'citadel"

---

### Post by HermanAB on 2008-01-29
Places like GoDaddy has the option to set MX records for a mail server.  In addition, also make sure that you have a functioning PTR record, since many mail servers do a sanity check on the PTR record to reduce spam.

BTW, you don't have to use Citadel.  Up to about 50 users, MS Exchange works pretty good on Windows 2003.
;)

Cheers,

Herman

---

