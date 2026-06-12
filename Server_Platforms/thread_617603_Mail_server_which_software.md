---
title: "Mail server which software"
date: 2007-11-19
forum: Server Platforms
---

### Post by mbuti on 2007-11-19
I'm configuring a server which will also act as a mail server.

After some studies I decided to use
fetchmail (to fetch from the external pop accounts) + postfix + procmail + spamassassin + clamav + dovecot(imap and pop)

Then I've read about amavisd-new, which looks nice, and dialogues directly in smtp.

So the question is, do I still need procmail if I use amavisd-new??

Because theorically amavisd-new gets directly from postfix and gives back the mail processed by the antispam filter and the antivirus.

Is my chain missing something?

I'm also using openldap with samba acting as PDC, but I haven't fully set up the ldap integration with mail services...
Thanks a lot

---

