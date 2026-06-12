---
title: "Is avaible rpm for spf(sender policy framework)"
date: 2008-01-15
forum: Server Platforms
---

### Post by dwhs.info on 2008-01-15
Does anyone know where i can found rpm and instruction for installing spf(sender framework policy)I noticed on their side it is integrated with latest version of ubuntu,but i have version 6.

---

### Post by kitterma on 2008-01-28
In Ubuntu we don't use rpms, but Debian packages.  Enable dapper-backports and apt-get install python-policyd-spf.  See the Ubuntu wiki for setup instructions.

---

### Post by MJN on 2008-01-28
Note however that you might wish to research SPF (pros and cons) to decide if it really is what you want.

I started using it a few years back and was a big supporter of it - I could see that as its use spread it would become more and more effective in the fight against spam.

However, the years have passed and it hasn't taken off much at all - indeed there are now more and more reason not to use it at all as it has many shortcomings. One of the most notable are the problems of using mail forwarders where those forwarders don't rewrite the message headers - this trips the SPF and ends up looking this spam.

Filtering outright with SPF (e.g. obeying -all settings) results in a load of false-positives given the above and so now whilst I've kept my SPF record I've dropped the -all. This makes it only effective for those anti-spam measures that use SPF as part of weighted spam filtering (like I now do) and so it's effectiveness is limited. This is perhaps reflected in the number of domains that have SPF records - the vast majority of those domains I see mail from don't. Even worse, many of those that do have been incorrectly configured (I've given up contacting mail admins pointing out why some of their mail gets bounced due to the erroneous configuration).

If I were you I'd think twice about whether or not you think SPF is going to help.

Mathew

---

