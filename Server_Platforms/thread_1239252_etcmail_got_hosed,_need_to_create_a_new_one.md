---
title: "/etc/mail got hosed, need to create a new one"
date: 2009-08-13
forum: Server Platforms
---

### Post by mohnkern on 2009-08-13
So I was an idiot, I admit it.

After having some problems with comcast and outbound email (basically comcast put my ip address on the spamhaus list, and insists that I route mail from my MTA (Sendmail) through them. I tried a workaround that completely messsed up my sendmail.cf and submit.cf files.  (They were the defaults.)

I forgot to make a backup, bad me.

I removed sendmail (apt-get remove sendmail), move /etc/mail to /etc/mail.old and figured when I did and apt-get install sendmail that it would put in the new configuration files, fixing my problems.

Alas, it didn't.  Is there a way to get apt-get or synaptic to rebuild the default configuration files in /etc/sendmail?

I tried:

apt-get purge sendmail
apt-get install sendmail

No luck.

---

