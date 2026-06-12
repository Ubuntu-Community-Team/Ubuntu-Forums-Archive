---
title: "Troubleshooting anacron"
date: 2009-04-24
forum: Server Platforms
---

### Post by botfish on 2009-04-24
I have a production server running Ubuntu 7.10. And was unable to get anacron working correctly. anacron was installed by default.

crontab was working fine. I successfully set it to send me an email every 5min by editing /etc/crontab.
I was able to manually force anacron to run with anacron -f

But there appeared not to be a link between crontab and anacron. I copied /etc/cron.d/anacron from my test server (Ubuntu 8.04) to my production server as /etc/cron.d/anacron did not exist on my production server.

Now anacron appears to be working. Have I done the correct thing in copying /etc/cron.d/anacron to my production server? Can somone explain to me why it now works?

> 
# /etc/cron.d/anacron: crontab entries for the anacron package

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

30 7    * * *   root	test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null


> 
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
14 * * * * root cd / && run-parts --report /etc/cron.hourly
33 0 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
55 2 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
29 1 19 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#



---

