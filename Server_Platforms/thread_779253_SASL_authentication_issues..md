---
title: "SASL authentication issues."
date: 2008-05-02
forum: Server Platforms
---

### Post by SuperCzar on 2008-05-02
I am working on configuring my first mail server.

Postfix/Courier are great at receiving mail on two domains, and delivering it to the appropriate virtual accounts.

SMTP is still non functioning. When I try to authenticate with through SASL I get the following error:
```
May  2 19:54:23 thirdrate postfix/smtpd[13102]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
May  2 19:54:23 thirdrate postfix/smtpd[13102]: warning: SASL authentication failure: Password verification failed
May  2 19:54:23 thirdrate postfix/smtpd[13102]: warning: [IP REMOVED]: SASL PLAIN authentication failed: generic failure
May  2 19:54:23 thirdrate postfix/smtpd[13102]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
May  2 19:54:23 thirdrate postfix/smtpd[13102]: warning: [IP REMOVED]: SASL LOGIN authentication failed: generic failure

```

I followed this guide: [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)

It seems to be only an authentication issue. Being that courier authenticates quite well, is there a way that I can use the courier authentication ala this guide :[http://gentoo-wiki.com/HOWTO_Email:_A_Complete_Virtual_System_-_SMTP_Authentication](http://gentoo-wiki.com/HOWTO_Email:_A_Complete_Virtual_System_-_SMTP_Authentication) (see the section on Cyrus-sasl to Courier-authlib to PostgreSQL).

**Cliff Notes:**

How do I fix my SASL -> mysql authentication? or how do I make SASL authenticate using the Courier authentication daemon?

---

### Post by SuperCzar on 2008-05-02
Just a quick update.  I did test sending from mutt on the local server, and it worked without issue.

I sent an email both to a local virtual email, and an email on another server, and both sent fine, so SMTP does appear to be working.

---

### Post by SuperCzar on 2008-05-02
well, I changed a few settings here and there, back and forth to try different things.

I symlinked some files into the chrooted directory, and all seems well.

Unfortunately, I cannot post exactly what fixed it, because I simply do not know.

---

