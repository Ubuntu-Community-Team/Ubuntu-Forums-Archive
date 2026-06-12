---
title: "logrotate"
date: 2009-06-17
forum: Server Platforms
---

### Post by vanderkerkoff on 2009-06-17
It seems that my automatic daily run of cron is not running my custom logrotate script for me, here's the custom file I made


vi /etc/logrotate.d/daughter_rails
# Rotate Rails application logs
/var/www/rails/daughter/shared/log/*.log {
  daily
  missingok
  rotate 7
  compress
  delaycompress
  notifempty
  copytruncate
}

And I checked the status of logrotate

cat /var/lib/logrotate/status
"/var/www/rails/daughter/shared/log/development.log" 2009-6-17
"/var/www/rails/daughter/shared/log/mongrel.log" 2009-6-17
"/var/www/rails/daughter/shared/log/production.log" 2009-6-17
"/var/www/rails/daughter/shared/log/searchd.log" 2009-6-17
"/var/www/rails/daughter/shared/log/searchd.query.log" 2009-6-17
"/var/www/rails/daughter/shared/log/test.log" 2009-6-17
 
But when I checked the directory none of the logs had been rotated.  /var/log/syslog did show the cron.daily running on that date, but it didn't have any mention of the daughter_rails script running.

I tested running the logrotate manually

sudo logrotate -f /etc/logrotate.d/daughter_rails

That worked and rotated the logs as expected

Oddly enough it did create a production.log.2.gz file on the first run, as if it was 'catching up' with missing a day or something.

Can anyone shed any light on this?  I'm going to leave it unchanged for now and see if it runs tomorrow morning, I think it might, but it's a bit odd it didn't run this morning.

Any help, greatly appreciated.

---

### Post by vanderkerkoff on 2009-06-17
ahh

I think I worked it out

I've appended the script to the /etc/logrotate.conf file instead and removed the /etc/logrotate.d/daughter_rails file and restarted syslog.

I was putting it in the wrong place :-)

dumbass

---

