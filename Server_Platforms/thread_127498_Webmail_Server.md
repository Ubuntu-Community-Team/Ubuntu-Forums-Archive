---
title: "Webmail Server"
date: 2006-02-09
forum: Server Platforms
---

### Post by christian8287 on 2006-02-09
Hi!

I want to make a webmail server on my home machine. I want that external mail addresses such as freemail.com, gmx.net, web.de, ... can send mails to my mail server and that mail accounts from my server (...@chk.at) can send to external mail addresses.

That should be realized over a web interface. How can I make this? I have heard, that I need courier for this.

Do I have to buy a mail domain or something like that? Does anyone have a howto for this?

Thanks!

with regards,
Christian.

---

### Post by sdamron on 2006-02-09
Hello,
First off, you will need to register a domain name, second, you will probably need some kind of dynamic DNS, but only if running this from your own cable or DSL type connection.  dyndns.org is a good one.  Second, you will need at a minimum, some kind of SMTP and POP3 server.  You can use IMAP (Cyrus, etc) with webmail, but you can also use something like openwebmail with just POP3.  Sounds like you need to do some digging and figure out which works best for your situation.  I personally use QMail, you can install from source, and it installs IMAP, POP3, SMTP and webmail all from one package.  The webmail is not very pretty tho.  You might think about either IMP/Hord, or Squirrelmail.  Very importantly, you will need control over at least your MX records for the domain you purchase.  You will for sure need to do some reading, alot about configuring, and securing the mail server after installation.  Nothing is worse than an open relay mail server!!!  HTH:-D

---

### Post by christian8287 on 2006-02-10
Thank you very much for your reply!

But I have still a few questions on this topic. I have an internet domain named chkloimuellner.ath.cx. This is a free one from dyndns.org. Are there any free mail domains, where I can register one? Secondly, I want to use the opengroupware software for webmail. So I think I need only qmail or something like that and use the account with opengroupware.

Thanks!

with regards,
Christian.

---

