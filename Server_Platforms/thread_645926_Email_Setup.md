---
title: "Email Setup"
date: 2007-12-20
forum: Server Platforms
---

### Post by lmahoney on 2007-12-20
Hello All,

I am currently in the process of implementing a mail server on Ubuntu server. We currently use Imail on Windows 2000. Approximately 40 domains with about 10 users per domain. Imail provides SMTP, POP, IMAP, web mail, spam filtering.

I've narrowed down my choices down to postfix and xmail. Can anybody provide their opinion/experiences with these?

Thank you.

---

### Post by HermanAB on 2007-12-20
Postfix and Qmail are the industry standards.

However, if you wish to set it all up in 20 minutes or less instead of two weeks or more, consider using Citadel instead.

Cheers,

Herman

---

### Post by lmahoney on 2007-12-20
Thanks for the reply Herman. Citadel looks very interesting. I'm definitely going to look further into it.

---

### Post by HermanAB on 2007-12-21
I have run a Postfix based system for 5 years and have now run Citadel for about 3 months.  I much prefer Citadel.  It is zero maintenance and just works.  

The Blue Citadel web theme looks OK with Firefox and it also works well with any mail client using the IMAP protocol.  I really have nothing to complain about with Citadel.  It is a no-nonsense, unobtrusive, easy to manage system.

Cheers,

Herman

---

### Post by lmahoney on 2007-12-21
HermanAB,

Can you provide some details? Such as hardware specs, number of domains and users. I'm finding if difficult finding any reviews and opinions on Citadel.

---

### Post by lmahoney on 2007-12-21
Nevermind HermanAB. I found some earlier posts of yours and others which were helpful. Thanks again.

---

### Post by Wizard of Aahz on 2007-12-21
lmahoney,

For a review of citadel, might I suggest Jon Watson's linuxjournal article from February 2007. 
 
 You can find a copy here.
 
 [http://www.linuxjournal.com/article/9357](http://www.linuxjournal.com/article/9357)

Enjoy.
- Aahz

---

### Post by HermanAB on 2007-12-21
Typically, you can run 10,000 users on the very same hardware that Exchange would need to support a few hundred users.

Cheers,

Herman

---

### Post by rsw686 on 2007-12-22
> **HermanAB said:**
> Typically, you can run 10,000 users on the very same hardware that Exchange would need to support a few hundred users.

Cheers,

Herman

I agree with this. I used to use Exchange 2000 and it would max out 1GB of memory with just a few users. I've moved to Postfix / Dovecot and the resource usage less than 1/3 of what is was before. Performance from the user end increased as well.

My setup uses Postfix configured for virtual users with mysql. I use Postfix Admin to manage the users. Dovecot works as the imap daemon.

It didn't take me more than a few hours to setup. I skipped spamassasian and clamav as I don't need that capability. Postfix can use rbls to block mail. I find that one a limited number of spam messages get through so I don't need bayesian filtering with spamassasian.

---

