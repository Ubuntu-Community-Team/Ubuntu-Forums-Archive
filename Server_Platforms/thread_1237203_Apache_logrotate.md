---
title: "Apache logrotate"
date: 2009-08-11
forum: Server Platforms
---

### Post by kenmiles on 2009-08-11
I have started to get the following error daily - 

/etc/cron.daily/logrotate:
error: apache2.bak:1 duplicate log entry for /var/log/apache2/access.log
run-parts: /etc/cron.daily/logrotate exited with return code 1 

so my log is not getting rotated but do not know how to find this duplicate log entry. I have renamed the log and started another but that does not cure it.

I am using Ubuntu 8.04 LTS and this is the apache2 logrotate file -

/var/log/apache2/*.log {
weekly
missingok
rotate 52
compress
delaycompress
notifempty
create 640 root www-data
sharedscripts
prerotate
/usr/lib/cgi-bin/awstats.pl -config=/etc/awstats/awstats.kmiles.co.uk.conf -update
endscript
postrotate
if [ -f /var/run/apache2.pid ]; then
/etc/init.d/apache2 restart > /dev/null
fi
endscript
}

Thanks in advance for any help, Kenneth.
[http://kmiles.co.uk](http://kmiles.co.uk)

---

