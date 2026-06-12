---
title: "please recommend an MTA"
date: 2006-09-16
forum: Server Platforms
---

### Post by sitedesign on 2006-09-16
can people recommend an MTA for me. We have used Sendmail and Postfix then manage them through webmin.

I would like a new mail server and we are looking at which MTA to use. The servers run about 300 email user accounts in about 100 domains.

I would still like a simple interface like webmin if possible. We would also like to be sure we can backup the settings easily for restoring on a new server if required, to cater for disaster recovery.

More background:
Our existing servers have used Dovecot for the POP3 and IMAP service, Dovecot has started giving issues with crashing on one of the servers and I am struggerling to solve it.
Sendmail was OK but tends to be a nightmare to set-up and the config files are hard for me to understand.
Postfix is again OK, the config was a little easier but the adding of virtual aliases was a bit ugly (or maybe just the webmin interface).

Exim I think is just the same as Sendmail but slightly modified.

We need to be able to include spam filtering (Spamassain) and virus scanning (ClamAV) Plus being able to put domain and email aliases into a file which are excluded from the filter process.

So we need an MTA which is easy to configure, maintain and pluggin to filtering. We also need ideas of POP3/IMAP servers.

No flaming please.

Updated:

Regards Peter King

---

### Post by lcg on 2006-09-16
> **sitedesign said:**
> can people recommend an MTA for me. We have used Sendmail and Postfix then manage them through webmin.

I would like a new mail server and we are looking at which MTA to use. The servers run about 300 email user accounts in about 100 domains.

I would still like a simple interface like webmin if possible. We would also like to be sure we can backup the settings easily for restoring on a new server if required, to cater for disaster recovery.

No flaming please.
Not meant to be a flame, but what is wrong with your previous solution? If sendmail and postfix worked and you are familiar with them, why not just continue using them?
Personally, I have never used sendmail and I never looked into graphical configuration tools, but both postfix and Exim worked nicely for me and their settings are easily backed up along with the rest of /etc/.

HTH,
Lars

---

### Post by sitedesign on 2006-09-17
I have updated my post to include more detail, hope it is a bit more meaningfull.

---

### Post by Child of Wonder on 2006-09-19
My recommendation would be Postfix.  We use at where I work and our ISP has about 50,000 customers.

I also use it at small businesses I do consulting for and on my home server.

If you need help with virtual accounts in Postfix I can link you to a guide.

---

### Post by intheory on 2006-09-19
I'b be interested in your guide , Child of Wonder, if you're still open to sharing. I'm looking for a strictly relay server for multiple domains, and am not quite sure where to start. Perhaps I should start a new thread....

I want to setup a server that I can define virtual domains on (foo.domain.com) and populate forwarding addresses for thousands of users (user@foo.domain.com -> [email]user@hotmail.com[/email]). We've been using CommunigatePro for this, but are having issues, and are interested in another solution. Any thoughts?

---

### Post by ff2k on 2006-09-20
I highly recommend Engarde Secure Linux:

[http://www.engardelinux.org](http://www.engardelinux.org)

It has almost everything you described:

secure web based interface for adding domains, accounts, managing dns,
has postfix

plus secure imap and secure pop.

---

