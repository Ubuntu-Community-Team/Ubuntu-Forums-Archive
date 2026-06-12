---
title: "Fix for cron silently aborting half-way"
date: 2012-05-24
forum: Server Platforms
---

### Post by dtfinch on 2012-05-24
For almost 2 years, I've been plagued by a mysterious problem on 10.04 where cron was only running the first few scripts in cron.daily and then aborting, without logging any cron related errors. I looked over all the scripts many times and found nothing that could cause it to abort.

Recently, I noticed that although cron hadn't logged an error, postfix did. "fatal: open /etc/postfix/main.cf: No such file or directory" Postfix was not installed by choice, but as a dependency of something else I needed to install (can't remember what) and having no intent to use it I skipped configuring it. But because it was there, cron tried to use it "automagically", the moment any cron script produced output (allowing the first few scripts to run fine), and when postfix failed, cron would silently abort without running the rest of the scripts. 

Running "dpkg-reconfigure postfix" and choosing the Local config and all the defaults was enough to fix the problem.

Posting it here so google can find it, because all the times I searched for this problem I found lots of others experiencing it, but not one solution.

---

