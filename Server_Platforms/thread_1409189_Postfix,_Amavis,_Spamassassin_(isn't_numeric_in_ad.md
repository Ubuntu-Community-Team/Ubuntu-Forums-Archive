---
title: "Postfix, Amavis, Spamassassin (isn't numeric in addition)"
date: 2010-02-17
forum: Server Platforms
---

### Post by isadjuk on 2010-02-17
Hello !!

I have got installed Postfix+Amavis+Spamassasin from "howtoforge howto"
In source message there isn't showing "spam score" i "spam-status" in header

Mail logs dont returns any errors, warnings.
Test patterns of virus and spam are blocked correctly.

There are errors after following command **/etc/init.d/amavis debug-sa** :

```
Feb 17 09:04:23.921 serv.serv /usr/sbin/amavisd-new[5787]: Creating db in /var/lib/amavis/db/; BerkeleyDB 0.34, libdb 4.6
Argument "4,235" isn't numeric in addition (+) at /usr/share/perl5/Mail/SpamAssassin/Plugin/AWL.pm line 348.
Argument "4,235" isn't numeric in addition (+) at /usr/share/perl5/Mail/SpamAssassin/PerMsgStatus.pm line 178.
Argument "1,673" isn't numeric in addition (+) at /usr/share/perl5/Mail/SpamAssassin/Plugin/AWL.pm line 348.
Argument "1,673" isn't numeric in addition (+) at /usr/share/perl5/Mail/SpamAssassin/PerMsgStatus.pm line 379.
Argument "1,673" isn't numeric in addition (+) at /usr/share/perl5/Mail/SpamAssassin/PerMsgStatus.pm line 178.
Argument "5,0" isn't numeric in numeric lt (<) at /usr/share/perl5/Mail/SpamAssassin/PerMsgStatus.pm line 1141.
Argument "1,0" isn't numeric in numeric lt (<) at /usr/share/perl5/Mail/SpamAssassin/PerMsgStatus.pm line 1141. 

```System is upgraded ofc ^^
I "googled" but didnt find a solution. What should I do ?

---

### Post by venol on 2011-04-24
yes, my problem same with you. The X-Spam-* header not shown on Email, but filtering message succesfful.

maybe somebody can help us?

---

### Post by venol on 2011-04-24
I find solution. Amavis insert X-Spam Header on email if the recipient listed in @local_domains_maps. Maybe this useful for someone. :)

---

