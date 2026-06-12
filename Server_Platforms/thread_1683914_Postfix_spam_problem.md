---
title: "Postfix spam problem"
date: 2011-02-08
forum: Server Platforms
---

### Post by jeculek on 2011-02-08
Hi!
I've managed to install and configure email gateway using postfix. exerything works fine but i have  one little (perhaps silly) problem - all the emails addressed to the non existent users are being blocked (as expected) however postfix sends back a 550 non delivery notification...the problem is that i get approx 100 000 spam emails a day and most of them are for the non existent users - now, can i configure postfix in a way that it doesn't send those notifications at all? 

cheers

---

### Post by cariboo on 2011-02-08
a bump for the move

---

### Post by SeijiSensei on 2011-02-09
Simplest solution is to create entries in /etc/aliases (using sudo) for the old addressees that directs their mail to /dev/null like this:

/etc/aliases
```

spamhound1:         /dev/null
spamhound2:         /dev/null

```

Then run "sudo newaliases" to rebuild the alias database file.  Now mail for spamhound1 will be accepted and delivered to a black hole.  No 550 will be generated since, from Postfix's point of view, the message was deliverable.

---

### Post by jeculek on 2011-02-09
Thanks for the reply but i'm being hit by the scrripts generating random prefixes to my domain address so there is no way i can make a list of aliases to by dumped to /dev/null. Somebody already asked me "yaaah...but if you disable it, how can the client for example know that he/she made a typo while sending an email to your user?"...tbh i don't give a crap, i just don't want those bastards fishing for the legit addresses to get any response at all.Does it make any sense? is it possible?


cheers

---

### Post by SeijiSensei on 2011-02-09
I don't know how you'd do it in Postfix.  In sendmail you can use [/etc/mail/access]("http://www.sendmail.org/m4/anti_spam.html#access_db") to build a list of valid To and From addresses for which it will accept mail.

I use an entirely different approach myself.  I have one machine that runs an ancient [store-and-forward SMTP proxy]("http://www.sourcefiles.org/System/Daemons/SMTP/smtpd-sd-1.3.tar.gz") with an excellent rules-based method for accepting or rejecting messages based on the SMTP envelope.  I can write rules that accept or reject mail based on the sending server address or domain and the To and From envelope addresses.  I drop about a third of the spam this way.  The rest I pass internally to another machine running [MailScanner]("http://www.mailscanner.info/") with [ClamAV]("http://www.clamav.net/") and [SpamAssassin]("http://spamassassin.apache.org/") for filtering and delivery.

---

