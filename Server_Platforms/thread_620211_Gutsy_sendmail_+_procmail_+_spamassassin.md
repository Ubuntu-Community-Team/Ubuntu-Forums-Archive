---
title: "Gutsy: sendmail + procmail + spamassassin"
date: 2007-11-22
forum: Server Platforms
---

### Post by ToniVC1963 on 2007-11-22
Hi,

I run a mail server with sendmail as MTA and procmail as MDA. As I'm getting loads of spam I'm testing SpamAssasin, which works perfectly well. But I still have some doubts.

First I tested SpamAssassin without spamd, and on a single user basis. Simply, I created a $HOME/.procmailrc file for each user wanting to user SpamAssassin, with the following contents:

```
:0fw
* < 100000
| /usr/bin/spamassassin
```

When receiving the first message, the $HOME/.spamassassin directory is created in each user's home directory. Then, the $HOME/.spamassassin/user_prefs file can be edited to modify SpamAssassin's behaviour as desired, so each user can decide how he wants it to work. That's ok, but you must create the .procmailrc file for each user, and the anyone can modify its own one...

Then, I decided to implement it system-wide instead of on a per user basis. I created a /etc/procmailrc file with the same contents as the local .procmailrc files seen before, but adding "DROPPRIVS=yes". Now, when receiving the first message the $HOME/.spamassassin directory is created too for each user getting mail. So, each user can still modify his $HOME/.spamassassin/user_prefs  to taylor SpamAssassin's behaviour as desired... but this can be troublesome!. (The "DROPPRIVS=yes" was needed because otherwise the $HOME/.spamassassin directory was created as root:mail instead of the correct userid and group for each user...).

My question is: whitout using spamd, how can I stablish a system-wide SpamAssassin behaviour without having to go and edit the $HOME/.spamassassin/user_prefs  for each user? Also, how can I disable future user changes on that file?

Also, I've experienced the system-wide approach but using spamc/spamd. I have many doubts about the implications (security and non security wise) of starting the daemon as root or as another user (say a newly created "spamd" one). I've made many tests, using the following /etc/procmailrc file:

```

DROPPRIVS=yes
:0fw
* < 100000
| /usr/bin/spamc
```

Starting spamd as root creates a .spamassassin directory in the root home directory, while starting spamd as user spamd creates it in the spamd user home directory. It seems logical, and moreover now there's only one single user_prefs file to modify to decide how will SpamAssassin behave for ALL users. But, still, what's best??

(Please, if reading the preceding explanation you think I've misunderstood something, make me know!)

Also,  I'm not sure about what's the best solution: using spamc/spamd or direct spamassassin calls. What would you advise?

Also, what would be the correct way to train SpamAssassin when using the system-wide spamd approach?

And finally, Is there any better way to use SpamAssassin with sendmail + procmail?

Thanks.

---

