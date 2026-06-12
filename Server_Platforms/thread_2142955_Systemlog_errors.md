---
title: "Systemlog errors?"
date: 2013-05-07
forum: Server Platforms
---

### Post by Valpskott on 2013-05-07
So, ever since I configured my ubuntu server so that it can send e-mails, I get scores of e-mails about errors. It's mostly been cron running my own scripts that has failed under some conditions, which I have fixed now.

What I need help with, are some error mails I get regarding the apache2 server I have running.

One error says:
> [ -x /usr/lib/p&#8203;hp5/maxlif&#8203;etime ] && [ -d /var/lib/p&#8203;hp5 ] && find /var/lib/p&#8203;hp5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/li&#8203;b/php5/max&#8203;lifetime) ! -execdir fuser -s {} 2>/dev/nul&#8203;l \; -delete

And this one pops up every 30 minutes:
> PHP Warning:  Module 'pdo_mysql' already loaded in Unknown on line 0
PHP Warning:  Module 'pdo_mysql' already loaded in Unknown on line 0

Any help or pointers would be much appreciated.

---

