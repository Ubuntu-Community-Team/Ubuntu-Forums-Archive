---
title: "Weird email from my mail server today (cron warnings/errors)"
date: 2014-11-30
forum: Security
---

### Post by Lido on 2014-11-30
I got an email today at root from my server that I don't think I've ever seen before.

```
Subject: Cron <root@myserver> test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```

```
/etc/cron.daily/amavisd-new:
Argument "perl_version" isn't numeric in numeric ge (>=) at (eval 517) line 1.
Argument "perl_version" isn't numeric in numeric ge (>=) at (eval 1010) line 1.
/etc/cron.daily/spamassassin:
Argument "perl_version" isn't numeric in numeric ge (>=) at (eval 620) line 1.
Argument "perl_version" isn't numeric in numeric ge (>=) at (eval 1113) line 1.
Nov 30 06:53:29.618 [7640] warn: Argument "perl_version" isn't numeric in numeric ge (>=) at (eval 558) line 1.
Nov 30 06:53:29.851 [7640] warn: Argument "perl_version" isn't numeric in numeric ge (>=) at (eval 1051) line 1.
```

Running 12.04 LTS with hardware enablement stack updated. Amavisnew email setup with postfix, dovecot, spamd etc.

Anyone else getting this message? I didn't set this cron up, so hopefully/presumably it's part of the default setup, but I've never seen this email before and I didn't update this week so I'm not sure what would make this warning show up all of a sudden. Hopefully not nefarious activity...

---

### Post by maniaq on 2014-11-30
me too - here is the fix (on Ubuntu you'll want to remove the 'vendor_perl' from the path):

[http://www.linuxquestions.org/questions/centos-*-111/%5Bsolved%5D-spamassassin-error-argument-perl_version-isn%27t-numeric-in-numeric-ge-%3D-4175526851/](http://www.linuxquestions.org/questions/centos-*-111/%5Bsolved%5D-spamassassin-error-argument-perl_version-isn%27t-numeric-in-numeric-ge-%3D-4175526851/)

(basically, install a patch from spamassassin)

---

