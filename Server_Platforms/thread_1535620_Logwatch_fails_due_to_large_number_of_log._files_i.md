---
title: "Logwatch fails due to large number of log.* files in /var/log/samba/"
date: 2010-07-21
forum: Server Platforms
---

### Post by Rich99 on 2010-07-21
I'm running Hardy Heron, and use logwatch to keep an eye on my logs.  Recently it has started failing - I get a long list of the files in /var/log/samba/, ending with:
| /usr/bin/perl /usr/share/logwatch/scripts/logfiles/samba/applydate| /usr/bin/perl /usr/share/logwatch/scripts/logfiles/samba/removeheaders>/tmp/logwatch.KfFGD4tH/samba failed: 65280 at /usr/sbin/logwatch line 967.
run-parts: /etc/cron.daily/00logwatch exited with return code 2

I know from previous experience that if I delete some files from /var/log/samba/ then it starts working again.  The files in /var/log/samba/ are individual files for each machine that samba has seen - of the kind log.hostname.  At last count there were 4112 of these files. 

What's the solution?  Presumably it's a bug in logwatch, and the workaround is to ensure I have less files in /var/log/samba/, but how do I do that?  Can I write a logrotate for log.*?  Will it accept wildcards?

---

