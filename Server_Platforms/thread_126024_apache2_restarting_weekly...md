---
title: "apache2 restarting weekly.."
date: 2006-02-05
forum: Server Platforms
---

### Post by sergio_101 on 2006-02-05
i have been having a problem with apache restarting weekly each week at 7:35AM on sunday morning..

i can't seem to find anything that points to anything in the crontab for this time, nor can i find anything in the error logs from apache to give me any clues..

maybe someone knows a reason why this would be happening?

any help is appreciated...

thanks!

here is some relevant info:

the last apache error log entry before restart:

[Sun Feb 05 07:35:17 2006] [notice] caught SIGTERM, shutting down

crontab entries:

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly

25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily

47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly

52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

last time since system reboot:

conveyor@Conveyor:/etc$ uptime
 14:00:02 up 24 days, 10 min,  1 user,  load average: 0.00, 0.00, 0.00

---

### Post by el3ktro on 2006-02-05
It's likely that you have a logrotate process, which backups&compresses your logfiles - after that, Apache has to restart. Look into /etc/cron.weekly if you find something about apache or logrotate.

IF it is really logrotate, then this behaviour is absolutely normal and nothing you have to worry about.


Tom

---

