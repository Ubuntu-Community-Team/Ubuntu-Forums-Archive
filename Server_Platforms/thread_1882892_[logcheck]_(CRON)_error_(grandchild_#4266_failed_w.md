---
title: "[logcheck] (CRON) error (grandchild #4266 failed with exit status 127)"
date: 2011-11-18
forum: Server Platforms
---

### Post by vincentvegan on 2011-11-18
Hi all,
for my Ubuntu 10.04 LTS server, logcheck send me this log:

Nov 14 08:10:01 *servername* CRON[4265]: (CRON) error (grandchild #4266 failed with exit status 127)
Nov 14 08:10:01 *servername* CRON[4264]: (CRON) error (grandchild #4267 failed with exit status 127)
Nov 14 08:20:01 *servername* CRON[4285]: (CRON) error (grandchild #4286 failed with exit status 127)
Nov 14 08:20:01 *servername* CRON[4284]: (CRON) error (grandchild #4287 failed with exit status 127)
Nov 14 08:30:01 *servername* CRON[4294]: (CRON) error (grandchild #4295 failed with exit status 127)
Nov 14 08:30:01 *servername* CRON[4293]: (CRON) error (grandchild #4296 failed with exit status 127)
Nov 14 08:40:01 *servername* CRON[4311]: (CRON) error (grandchild #4312 failed with exit status 127)

this is an error of execution to cron [127 = command not found].
   if I run the command "crontab -l" for each user, I do not see any cron to any user
   you have any ideas?

---

