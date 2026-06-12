---
title: "New install of 16.04 - Postfix/Dovecot - deliverying to wrong folder?"
date: 2016-06-23
forum: Server Platforms
---

### Post by jimwillsher on 2016-06-23
Background: I have a fuly working 14.04 mailserver installation, and want to set up a clean 16.04 equivalent setup. LAMP, Postfix, Sieve, Dovecot etc.

Everyting is working on my 16.04 install EXCEPT for emails. If I send a mail from outside to a lcoal user, the mail ends up in /home/username/Maildir/new. On my old 14.04 system is arrives in /var/mail/username

The $MAIL variable on the new system is pointing to /home/username/Maildir. On the old 14.04 it's pointing to /var/mail/username


I've no real preference for whether the emails go to /home/username/Maildir or /var/mail/username, I don't care. But the problem is that on the new system, Squirrelmain and MS Outlook (via dovecot) are both looking for mail in a palce where there is no mail :-) I am guessign that they are looking in  /var/mail/username but the new mails are in /home/username/Maildir.

I have a /etc/dovecot/conf.d/99-mail-stack-delivery.conf file containing

  mail_location = maildir:~/Maildir

which I also had on the 14.04 box.


Can someone suggest what may be the cause? I guess the underlying issue is the $MAIL variable but I'm not certain, since the /home/username/Maildir approach has one fiel per messages whereas the /var/mail/username approach does not, so simply changing the variable (somewhere?) may not be the answer.


Very appreciative of any help.

Many thanks



Jim

---

### Post by howefield on 2016-06-23
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by jimwillsher on 2016-06-25
I gave up, as I never got it to work and have lost interest in it now. I'll  stick to 14.04 whilst I rethink my email strategy.

---

