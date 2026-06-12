---
title: "Postfix Dovecot listen to mail.domain &amp; smtp.domain"
date: 2012-01-30
forum: Server Platforms
---

### Post by Wouter_DS on 2012-01-30
Hello,

I have followed and installed [this]("http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid") tutorial perfectly and everything works as it should work.

But how do I make the mail server listen to the subdomains mail.domain.com and smtp.domain.com? So I can connect to it from my mail clients on my laptop etc..
I do receive the emails on the server.
[IMG]http://f.cl.ly/items/1B1U0N2S0e24311k0U03/Screen%20Shot%202012-01-30%20at%2017.40.20.png[/IMG]

I'm running Ubuntu 10.04 Lucid LTS 32bit

Thanks in advance,
WouterDS

---

### Post by Wouter_DS on 2012-01-31
Oops. I now realized that I haven't set the DNS yet.

I have now set my DNS like this (is this correct?).
[IMG]http://f.cl.ly/items/2t0W0O262n1c2J1T1H0x/Screen%20Shot%202012-01-31%20at%2012.26.12.png[/IMG]

But still no luck.

This is what I expected to see (tried it on the localhost)
[IMG]http://f.cl.ly/items/1L0J0Z081c392P3p1Y1k/Screen%20Shot%202012-01-31%20at%2012.27.15.png[/IMG]

This is what I get to see (remote, from home)
[IMG]http://f.cl.ly/items/40230O3h2o2z2v2F1H2r/Screen%20Shot%202012-01-31%20at%2012.39.56.png[/IMG]

Thanks

---

### Post by Wouter_DS on 2012-01-31
OMG.
I have found it.

Every ISP in my country has to block port 25 by law.
Sorry for this useless post.

Regards,
WouterDS

---

